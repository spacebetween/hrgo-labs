---
title: "My Introduction to SVG's and FIVE Reasons Why I’ll Be Using Them in the Future"
date: 2017-11-30T13:20:20.684Z
draft: false
---

I recently had the pleasure of building [TEDx Folkestone](http://www.tedxfolkestone.com/), designed by [Flourish Studios](http://weareflourish.com/). I really loved the design - it’s modern and I love the big fonts and quirky graphics that give the whole website some personality. Being such a fan of the design I really wanted to do it justice when I was building the site, especially with the translucent graphics that show throughout.

I had to create this graphic, half of a red translucent X, that would be positioned to the right of the page.

![](https://images.prismic.io/spacebetweenweb/c0df35f5b6e168156ba193979b6a28e927e2da16.png?auto=compress,format)

I didn’t want it to be a JPEG/PNG, as it had to be scalable and I didn’t want the image to lose any sort of resolution on smaller screens. My solution to this was to use CSS to create the shape. I had made shapes in CSS before, I didn’t think this would be too different\! I could set the transparency, have control over how it resizes on small screens with media queries (what was I thinking) and I would feel really clever for doing all of this in code.

![](https://images.prismic.io/space-between%2F98df53cc-f038-4968-85bc-7c5dbc39c41b_stupid.gif?auto=compress,format)

*Me @ past me for considering media queries and css as a solution*

Of course, doing this in CSS was not the most efficient way. It involved a lot of pseudo elements, a lot of negative positioning, empty divs on the page. It was frustrating and I was wondering why I was putting myself through this. I asked for some help and Luke said “Why don’t you use SVG’s? It'll scale nicer and also have really good [browser support](https://caniuse.com/svg)”.

The reason, is simply I just hadn’t considered it before\! I had never really worked with them before and my only exposure was following [Sara Soueidan](https://twitter.com/SaraSoueidan), one of the most influential SVG writers, on Twitter. I knew that they were a way of creating images and animations but I wasn’t sure why/when I would use them over my usual image formats. Until now\! I saw this as a great opportunity to learn something new and anything that scales nicely and has good browser support is definitely worth picking up\!

![](https://images.prismic.io/space-between%2Ffa9088df-4052-48ac-b686-607847797081_mind-blown.gif?auto=compress,format)

*A solution that offers scalable, customisable and small sized images? Mind blown*

I was able to create the SVG xml files using the [Sketch App](https://www.sketchapp.com/) free trial. In Sketch, you can create an image/symbol and then convert that symbol into an SVG. If I didn’t have Sketch, I would use an online conversion tool, that would cleverly pick out all of the lines/co-ordinates of an image and give you them in XML. A great example is [Vector Magic](https://www.vectormagic.com/). SVG conversions work better on 2 dimensional images that are quite flat in design, like illustrations and symbols. For images that have a lot of complexity, and are colour heavy like a photograph it is better to stick with PNG/JPEG type images.

After a lot of help from my team I had a set of graphics, that looked great and true to the design\!  
Here are my reasons why for future projects, I will be thinking SVG first\!

1.  Customisable/ Style with CSS -  
```
With SVG’s you can add classes and styles, so rather than have different images for different coloured graphics you can add classes that change the colours instead. This was really helpful for me, as depending on the template my graphics had the change colours. I could do this with code without having to have a different image for each template.
```
2.  SEO  
```
As SVG’s are text based and written in an XML, when you use the \<text\>\</text\> tag in an svg document, this gets indexed by Google. Normal images don’t have crawlable text.
```
3.  Compatibility  
```
SVG’s are supported in browsers of all size, and all browsers have a basic support of SVG’s
```
4.  Scalable  
```
SVG stands for Scalable Vector Image, and because it is vector based it can adjust to any resolution and you’re not restricted with pixels
```
5.  Small file sizes  
```
PNG’s can end up as very large file sizes, especially when they’re big in size and high definitions. As SVG’s are text based, you can expect that they are smaller. In the example below, you can see that the SVG is 25KB, and the PNG of the image is 89KB.
```

![](https://images.prismic.io/spacebetweenweb/8d340e62b61a26a97620073ac69cd9700b08781c.png?auto=compress,format)

![](https://images.prismic.io/spacebetweenweb/894190a010d8ee770a9c187d849afd7d7da33e78.png?auto=compress,format)

To learn more, have a look at this SVG course from CSS Tricks: <https://css-tricks.com/lodge/svg/> I still have a lot to learn and I look forward to blogging about SVG’s in the future\!  
