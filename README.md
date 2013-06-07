meteor-popcorn-js
=================

Meteor packaging of the library Popcorn.js (by Mozilla) for integrating the web into video production.

Check out the documentation [here](http://popcornjs.org/popcorn-docs/).

### Installation
===

Install the package through *meteorite*: `mrt add popcorn` 

### How to use it in Meteor
===

If you want to use Popcorn.js to create a player inside a *div* which is contained in a template named *myTemplate*, we have to use the `Template.myTemplate.rendered` callback to make sure the call to Popcorn.js is only executed once the HTML element we want to target has been rendered.

Here is a basic example:

	
	<!-- app.html -->
	<head>
  		<title>myApp</title>
	</head>

	<body>
		{{> myTemplate}}
	</body>

	<template name='myTemplate'>
		// HTML element where the Popcorn video will be inserted in
		<div id='youtube-video'></div>
	</template>


Then in your JavaScript file:

	// app.js
	if (Meteor.isClient) {
		
		Template.myTemplate.rendered = function () {
			var video = Popcorn.youtube('#youtube-video', 'http://www.youtube.com/embed/lSAKFkxq4jA');
		}
		
	}
	

