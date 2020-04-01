---
title: "A git process to avoid a cherry-pick apocalypse"
date: 2020-04-01T07:54:12.138Z
draft: false

---

If like us you work on projects with multiple long-running branches (we use the master branch for production, and a staging branch for QA), then you may have issues with merge conflicts, or worse still silently losing changes, when cherry-picking changes between stage and master.

To quote Raymond Chen from the [Microsoft developer blog](https://devblogs.microsoft.com/oldnewthing/20180312-00/?p=98215)

> Cherry-picking is a common operation in git, and it’s not a good idea. Sometimes it’s a neutral idea, but I haven’t yet found a case where it’s actually good.

You can come across this problem when you want to deploy some of what is in your stage environment into production.

Here's a stripped-down example to clearly define what can go wrong:

```bash
» mkdir git_demo
» cd git_demo
» git init
» echo '{"important_feature_flag": true }' > config.json
» git add .
» git commit -m "Initial commit"
[master (root-commit) 81bbc8a] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 config.json
```

Our master branch now has a single config commited. We switch to a new feature branch.

```bash
» git checkout -b feature-1
```

We realise we want to turn the feature off as there is a bug. So we commit to the feature branch and cherry-pick the change into master.

```bash
» echo '{"important_feature_flag": false }' > config.json
» git commit -am "Turn off important feature"                                                                                                                 [feature-1 71488a7] Turn off important feature
 1 file changed, 1 insertion(+), 1 deletion(-)
» git checkout master
Switched to branch 'master'
» git cherry-pick 71488a7
[master 9a96935] Turn off important feature
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Later when working back in the feature branch, we fix the feature and enable the feature flag again.

```bash
» git checkout feature-1
Switched to branch 'feature-1'
» echo '{"important_feature_flag": true }' > config.json
» git commit -am "Fixed bug - turn on feature"
[feature-1 9a64de0] Fixed bug - reenable feature
 1 file changed, 1 insertion(+), 1 deletion(-)
» git checkout master
Switched to branch 'master'
» git merge feature-1
```

We've now merged our feature into the master branch. What do you expect the feature branch to be set as in master - on or off? As we fixed it in the feature branch and have merged it in we expect that the flag will be set to true in the master branch, but that change is lost:

```bash
» cat config.json
{"important_feature_flag": false }
```

For a deep dive into what goes wrong here you can read the full blog series on the [Microsoft Developer Blog](https://devblogs.microsoft.com/oldnewthing/?p=98225).

## A process to avoid cherry-pick problems

In this example we want to merge *some* commits from stage into master, in a way that doesn’t create merge conflicts and general chaos further down the line when a straight merge is done between the two branches.

To begin, let's make sure both of our local branches are up to date:

```bash
git checkout stage
git pull origin stage
git checkout master
git pull origin master
```

Then we need to know the common ancestor for both branches - git calls this the merge base, and it is the point at which the two branches have begun to differ.

```bash
git merge-base master stage
> 1545c0272366aba19e77fa095d847c753e1cf9c0
```

This outputs a commit ref - you can do git show 1545c0272366aba19e77fa095d847c753e1cf9c0 to see more details about it.

Now we will checkout a new patch branch which is based on this merge base.

```bash
git checkout -b patch-branch 1545c0272366aba19e77fa095d847c753e1cf9c0
```

At this point if it is just 1 or 2 commits that we want to be merging, we can cherry pick those commits into our patch branch.

```bash
git cherry-pick <<commit ref 1>>
git cherry-pick <<commit ref 2>>
```

If more commits need to be brought in which makes individual cherry picks impractical, then an interactive rebase can be used to add a list of new commits to the patch branch. First you merge in all the commits from stage, then do an interactive rebase to rewrite the history and drop the commits you don’t want to be merged in.

```bash
git merge stage
git rebase -i 1545c0272366aba19e77fa095d847c753e1cf9c0
```

Now that patch-branch has just the commits you are interested in, it can be merged into master.

```bash
git checkout master
git merge patch-branch
```

This next step seems unnecessary but is important as it will update the merge-base for the two branches. You now also merge your patch-branch into stage - this should add no new changes to stage, but by updating the merge base will allow any future merges between the two branches to go smoothly.

```bash
git checkout stage
git merge patch-branch
```

Lastly, push all your changes to the remote.

```bash
git push origin stage:stage
git push origin master:master
```

Happy merging!
