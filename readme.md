#External.js
By: Jan Schoepke (janschoepke@me.com), originally by Cal Evans (cal@calevans.com) 

License: MIT

This is a plugin for Reveal.js. It allows you to specifiy external files to be loaded into a presentation. This extension also allows external files in already external files (Subfiles). It allows a course, which may be hundreds of slides, to be broken into modules and managed individually. 

#Using external.js

Using the plugin is easy. First, register it in your Reveal.initalize block.

```
{ src: 'plugin/external/external.js', condition: function() { return !!document.querySelector( '[data-external]' ); } },
```
Then simply add an element into your presentation with a data-external attribute.

```
<section data-external="module_01/index.html"> </section>
```

If you want to load external files, you have to choose relative paths in the "data-external"-attribute. In the following there is a simple example of how to include many files in one reveal presentation: 

Folder structure: 

- __includes__
	- __chapter1__
		- 	__chapter1_1__
			- index1_1.html 
		-  __chapter1_2__
			- index1_2.html 
		-  index_1.html
	- __chapter_2__
		- index_2.html
	- __chapter_3__
		- index_3.html
- index.html

Code of index.html: 

```
...
<div class="reveal">
    <!-- Any section element inside of this container is displayed as a slide -->

    <div class="slides">
         <section data-external="includes/chapter1/index_1.html"> </section>
         <section data-external="includes/chapter2/index_2.html"> </section>
         <section data-external="includes/chapter3/index_3.html"> </section>
    </div> <!-- slides -->

</div> <!-- Reveal -->
...
```

Now you may wish to include the subchapters 1.1 and 1.2 to the content of chapter 1. This would be the code of index_1.html:

```
...
	<section data-external="chapter1_1/index1_1.html"> </section>
	<section data-external="chapter1_2/index1_2.html"> </section>
...
```
Remember that all the paths entered in "data-external" were relative!

It is also possible to include files outside of _section_-tags, as this would result in seperate slides. If you don't want the included content to be a new slide, you can include the content to another element, too (e.g. a _div_).

```
...
	<div data-external="chapter1_1/index1_1.html"> </div>
...
```