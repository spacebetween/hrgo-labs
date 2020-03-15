---
title: "Tackling Universal Javascript"
date: 2017-11-30T13:06:50.293Z
draft: false
---

Simply put, ‘Universal Javascript’ is javascript that is capable of running on both the browser and the server, but also on native devices, embedded systems and more.

It’s also referred to as ‘Isomorphic Javascript’ as there [is some confusion](https://medium.com/@ghengeveld/isomorphism-vs-universal-javascript-4b47fb481beb#.qynvprq3b) regarding what ‘universal’ and ‘isomorphic’ mean in the context of Javascript. [It was decided by community leaders](https://medium.com/@mjackson/universal-javascript-4761051b7ae9#.difdd2cgz), that, in fact, it’s best to call it Universal.

 So, now we’ve cleared that up, let us move on.

## Why Universal Javascript?

The reason the decision was made to use Javascript say instead of say C\#, PHP, or any other popular server-side language is because javascript allows the junior members of our team (including me) to use our front-end skills in a more productive way. This grants us the ability to be introduced to powerful concepts such as [REST](http://rest.elkstein.org/), and [HTTP](https://varvy.com/http/basics.html), without the added mental stress of learning a whole new language, abstracting away from the language itself and focusing on the concepts behind what’s happening on the client, and the server.

It’s a great environment to develop and nurture both front-end and back-end skills, and removes the necessity of context-switching, leaving us to think about the important parts of our application rather than the implementation details, and stressing over semi-colons.

Furthermore, another selling point of universal JavaScript is the fact that it runs on every device. iPads, iPhones, Android, Raspberry Pi’s...  whilst, PHP for example, can not. This, I believe, gives Javascript a unique ‘future-proofed’ status among programming languages, as it provides us the freedoms of using experimental javascript and device features without being limited by the browser, allowing us to create cutting-edge solutions for our clients, as the language evolves. Also, given that Universal Javascript is in it’s relative infancy; it has some huge industry backers. These include [Netflix](https://www.infoq.com/news/2015/08/netflix-universal-javascript), [Airbnb](https://nerds.airbnb.com/isomorphic-javascript-future-web-apps/) to name a few.

Universal Javascript also gives us the added benefit of a substantial performance boost. The templates created in our components can be rendered on the server; and plain HTML can be sent the client. This benefits the user greatly; as it will provide them with a viewable media faster, without relying on fast loading speeds, location, device speed or any other of the factors regarding the user's experience outside of our testing environments. This, in turn, reduces the [bounce back rate](https://support.google.com/analytics/answer/1009409?hl=en), providing more conversions for marketers. More benefits include ‘[perceived speed](http://blog.teamtreehouse.com/perceived-performance)’, which is where the user *thinks* your site is faster than it actually is; this can be achieved by critical CSS rendering; which is where the ‘above the fold’ content is rendered as quickly as possible, which in turn gives the user the content that they want, faster.

Universal Javascript also offers SEO benefits. One of the biggest disadvantages to building a Single Page Application (SPA), is the fact that it’s all rendered on the client. What does this mean? Well, this means that google's, bing's, and yahoo's’ webpage crawlers aren’t able to interpret client side code; because they crawl the server pages. However, with Universal Javascript, these pages can be pre-rendered on the server, giving accurate content to the crawlers.
