#Webapp-base


This is my base package for a fron-end heavy webapp. This package is completely 
backend agnostic, when you deploy it as is it makes no assumptions about your
back-end, it will work in any modern browser out of the box.

**NOTE:** This base contains coffeescript it is not dependant on it but it is
included as a default since I use it. (so having coffeescript installed on your
development environment helps you take full advantage of this)

##Contents

* [html5-boilerplate](http://html5boilerplate.com/) 
	used for general structure, build scripts and a nice base to start from

* [jQuery v1.6.4](http://jquery.com/) because it's jQuery, can't live without it
* [Backbone.js](http://documentcloud.github.com/backbone/) provides the model-view-collections framework and a lot of building blocks
* [CoffeeScript](http://jashkenas.github.com/coffee-script) just to make javascript a lot nicer.
* [less](http://lesscss.org/) to make writing css a bit nicer.


##Cakefile

There is a cakefile with 3 task to ease building. The tasks are:

*  `cake build` concatenates (in the order of: Models first, then collections, then views and finally main.coffee) and builds it all into a app.js file.
*  `cake buildCss` builds the style.css file based on style.less
*  `cake watch` watches for changes in either src or css folders and then builds a new css or js file depending on which changed

**These files use growlnotify for notifications, that might require some tweaking on non OS X computer**
