---
layout: post
title: "A Semantic Kind of Blue"
date: 2012-07-25 17:59
comments: true
categories: css sass
---

Reading [MVCSS](http://mvcss.github.com/MVCSS/#global) (by [Drew Barontini](http://twitter.com/drewbarontini) and [Nick Walsh](http://twitter.com/nickawalsh))

> ... we definitely recommend two things when making use of Sass variables: prefix the variable with what it represents ($color-base, $color-highlight, $font-base) and make use of semantic names ($color-base rather than $color-blue).

prompted me to share my own adventures in naming SCSS colors.

### Tl;dr

Colors on your website usually have multiple uses so choosing a variable name that describes them well is too hard. You are better off sticking with a variable name that describes what your eye will see. The most semantic name for #0000FF is blue.

## "Semantic" Names

The standard best practice on color names in Sass goes something like this:

```scss
// Define a color palette
$color-base: rgb(0, 0, 240);
$color-highlight: rgb(250, 10, 10);

// Refer to color variables as required
.something {
	color: $color-base;
}

.something-important {
	color: $color-highlight;
}
```

This is generally thought of as creating "semantic" names for each color i.e. we associate a label with our color that communicates some extra, **useful** information about it. For example, ```$color-highlight``` tells us that this color is used as some sort of highlight on the site. So far, so best practice.

However in my experience, it is extremely rare for one color to have a single use-case on a website. Most websites have a small-ish (less than 10) color palette. The same color could be part of a gradient in the background as well as indicating the hover state of the largest buttons on the site. This makes choosing a name for your color that will communicate some **useful extra meaning** a *lot* harder. Let's look at a more realistic example:

```
$color-highlight: rgb(250, 10, 10);

.btn-large:hover {
	background-color: $color-highlight; // Good match. this is indeed a "highlight"
}

.page-banner {
	background-color: $color-highlight; // Hmmm not exactly a "highlight"
}

.btn-massive {
	border: 1px solid $color-highlight; // Oh dear, this isn't a highlight at all ...
}

.btn-massing:hover {
	border: none;
}

```

Being of sound mind, you dismiss ```$color-page-banner-bg-but-sometimes-btn-hover-too``` as a bad idea but you might (as I did) think that you can solve this by simply creating a separate "semantic" variable name for each use-case that will convey useful information to the reader.

```
$color-page-banner-bg: rgb(0, 0, 230);
$color-btn-massive-border: rgb(0, 0, 230);
$color-btn-large-hover: rgb(0, 0, 230);

// Hmmm we seem to be trying to re-invent CSS selectors in our variable names ...
```

Great. Except that you have now commited to creating a new variable for **each** and **every** use of a color on your site. Hope you like typing because on a medium/large site this will be a *long* list of single-use variables. Oh and unless your variable names are specific enough, they will create more confusion than they solve.

There are instances where this would be desirable behaviour e.g. you have a site that you wish to create a number of "themes" for - Shopify does something like this with it's themes, allowing you to change all the colors in one place. However in most cases, this functionality is not required so all we have really done is insert another level of abstraction into our code.

Now let's consider

```
$color-blue: rgb(0,0,230); // I am a blue.

.btn-large:hover {
	background-color: $color-blue; // Reads nicely eh.
}

.page-banner {
	background-color: $color-blue; // Yep, also a blue
}

.btn-massive {
	border: 1px solid $color-blue; // No worries here either.
}

.btn-massing:hover {
	border: none;
}
```

This variable name makes no attempt to tell us where it is used - it simply declares that it is a color and it some sort of blue. If a new dev wants to change the look of a particular seciton of code, she finds the selectors that match and change the rules - she doesn't have to figure out your variable naming scheme. Happy days.

As an added bonus, your color variables are named in the way that your team talks about them - teams speak of "our blue" or "the red" etc. You also don't have any conceptual weirdness when you use the same color on a button highlight and a background.

And anyway, in what world is "blue" not semantic for that portion of the electromagnetic spectrum that the human eye percieves as blue?

But what if we need a drastic color change? Say the design team decides the blue should become red? Won't I need to search & replace all instances of the variable? Yes. But it's ok because that happens very rarely in my experience. What happens much more frequently during development is small changes to colors and these are not a problem - I'm pretty happy to continue calling it blue as long as it looks mostly blue.

## Conclusion

Because designs re-use the same color in so many ways, coming up with variable names that describe how/where they are used is too hard and introduces an unnecessary and unhelpful level of abstraction. Simple FTW.

#### Am I wrong?
It's happened before. Educate me in the comments.