---
layout: post
title: "Not your grandad's progressive enhancement"
date: 2014-04-12
comments: true
categories:
---

TL;DR Progressive enhancement does *not* mean that everything has to make sense as a document.

I really enjoy [The web ahead](http://5by5.tv/webahead). In [episode 65](http://5by5.tv/webahead/65) [Jen Simmons](https://twitter.com/jensimmons) and Simon St. Laurent chat about the influx of new folks working on the web and voice their concerns about the values these new people bring. Jen has also [blogged about this](http://jensimmons.com/note/2014/04/09/web-ahead-triple-play).

My perspective on this is as somebody with a foot in both camps here having started as a front-end dev, drifted over to the server and now alternating between both.

Back in the day, the web standards movement advocated for standards compliant, cross device, appropriately semantic way of styling and presenting content. Javascript existed but its role was peripheral, acting as a layer of optional niceness.

And they won. The tenets of web standards are now the accepted way to build websites. Now the success of the web as a publishing platform has opened a new frontier - that of the application development platform.

### Progressive enhancement revisited

The central idea that the HTML document should make sense without anything else just doesn't make sense to folks making web applications. The "job to be done" of a content based site is to get that content from the screen into the brains of readers. This is a job that HTML is capable of doing by itself (season with CSS and JS to taste).

Consider a "Photoshop" alike web application as indicative of the complex, ambitious things we are trying to build on the web now. The jobs to be done here might be:

* _cut this image up into 3 pieces_
* _adjust the blue in this image to match our logo_
* _combine this image with our logo and a message_

These jobs cannot be satisified by HTML. HTML can certainly display an image on the screen but there is no version of "show the image on the screen" that is an acceptable fallback when you want to achieve one of the tasks above.

Progressive enhancement does *not* mean that everything has to make sense as a documment. That definition worked for us in the past but doesn't help people making large, complex web applications. We cannot consider Javascript as "sugar on top" even if we wanted to.

### What to do

There _is_ an influx of new people working on the web. There are a whole new set of people who have yet to learn that, for all its technical limitations, web workers hold themselves to a high bar.

But also we need to be patient with the new folks. Application development on the web is immature and damn hard right now. It took us a long time to figure out how to put documents on the web so it seems reasonable that in learning to put applications on there, we will make mis-steps too.

Those of us who have been working on the web for long enough are responsible for communicating the values that are the best of the web. If we are to be successful in this then the 2014 web standards message can't _just_ be a cut & paste from 1998.

Time to find that old blue beanie again and get to learning & teaching.
