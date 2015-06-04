<span style="color: red; font-weight: bold;">NOTE: This content is for LSCC tutorial/workshop authors.  It is not useful to tutorial/workshop attendees</span>

# Showable extension demo

A simple component that allows you to have hidden Markdown section (called the body) that is revealed when the user
clicks on the title link






## Minimal

In it's simplest form *\showable* applies very minimal styling to the HTML (though lots of classes for
your convenience)

**syntax**:

```md
\showable{Title text}

This is the text that will show

\endshowable
```

**example**:

\showable{Title text}

This is the text that will show

\endshowable

**html**:

When the showable is shown the *showable-hidden* class is removed from the top-level div tag

```html
<div class="showable-container showable-hidden" id="showable0">
	<div class="showable-inner">
		<div class="showable-header" id="showabletitle0">
			<a href="" id="showablelink0">Title text</a>
		</div>
		<div class="showable-body" id="showablebody0">
			<p>This is the text that will show</p>
		</div>
	</div>
</div>
<script>
$(document).ready(function(){
    $("#showablelink0").click(function(){
        $("#showable0").toggleClass("showable-hidden");
        return false;
    });
});
</script>
```






## Partial title link

If you put text around the *\showable* tag then it will be included with the title link

**syntax**:

```md
Click \showable{here} to reveal a secret

If you put text around the \showable tag then it will be included with the title link

\endshowable
```

**example**:

Click \showable{here} to reveal a secret

If you put text around the \showable tag then it will be included with the title link

\endshowable

**html**:
```html
...
		<div class="showable-header" id="showabletitle1">
			Click 
			<a href="" id="showablelink1">here</a>
			to reveal a secret
		</div>
...
```






## Markdown ##

You can include markdown in the body of the showable

**syntax**:

```md
\showable{Show me the magic}

* **WOW**: its bold text in a list
* that includes more than one item 

\endshowable
```

**example**:

\showable{Show me the magic}

* **WOW**: its bold text in a list
* that includes more than one item 

\endshowable







## CSS Classes ##

You can include an extra section on the *\showable {TITLE}{CLASSES}* tag to specify a CSS style to apply to the showable sections.  
You can specify more that one class by separating each by a space.  Each class is applied to the 3 sections: *container*, *header* and 
*body*.

**syntax**:

```md
\showable{Custom CSS}{example}

A showable with custom CSS class applied
 
\endshowable
```

**html**:

```html
<div class="showable-container showable-hidden example-container" id="showable3">
	<div class="showable-inner">
		<div class="showable-header example-header" id="showabletitle3">
			<a href="" id="showablelink3">Custom CSS</a>
		</div>
		<div class="showable-body example-body" id="showablebody3">
			<p>A showable with custom CSS class applied</p>
		</div>
	</div>
</div>
```







### Builtin CSS classes ###

There are a number of builtin showable CSS styles

**syntax**:

```md
\showable{Question}{question}
\showable{Hint}{hint}
\showable{Answer}{answer}
\showable{Indent}{indent}
```

**example**:

\showable{What is the answer to life?}{question}

Some more details of the task at hand; "not dying"
\endshowable


\showable{Hint}{hint}

What is the answer to everything?
\endshowable


Show \showable{Answer}{answer}

**42**

You really should use the Showable extension for LSCC Tutorials 
\endshowable


\showable{Note}{indent}

If you want the showable text to line up with the other builtin classes use *indent* class
\endshowable


\class{Is the Showable Extension awesome?}{question}







## Nested showables ##

You can put showables inside each other.

**syntax**:

```md
\showable{Hint}{hint} there is more to me inside

You can stack showables inside of me

Click here to see \showable{more} hints

**And what have we here**

\endshowable

\endshowable
```

**example**:

\showable{Hint}{hint} there is more to me inside

You can stack showables inside of me

Click here to see \showable{more} hints

**And what have we here**

\endshowable

\endshowable








## Alternating title link ##

The title link text can be swapped depending on what state it is in.  To specify the alternate (when shown) title link
text add it to the end of the title and separate with a pipe-symbol (|).

**syntax**:

```md
\showable{More|Less}{indent}

Are you sure you want to know more?

\endshowable
```

**example**:

\showable{More|Less}{indent}

Are you sure you want to know more?

\endshowable








## Inverted ##

If you want the showable to be initally visable you can by adding a plus (+) after the *\showable*

**syntax**:

```md
Click to \showable+{Hide}{indent}

This content will be initially open and can be closed by click on title

\endshowable
```

**example**:

Click to \showable+{Hide}{indent}

This content will be initially open and can be closed by click on title

\endshowable









## No content ##

If the showable has no content then the title link is replaced with a span and no body section is added.
The span tag has the added class *link-like*.

**syntax**:

```md
A \showable{Showable}{indent} with no content

\endshowable

ALT:

A \showable{Showable}{indent} with no content\endshowable
```

**html**:
```html
<div class="showable-container indent showable-hidden" id="showable11">
	<div class="showable-inner">
		<div class="showable-header indent" id="showabletitle11">
			A 
			<span class="link-like" id="showablelink11">Showable</span> 
			with no content
		</div>
	</div>
</div>
```

**example**:

A \showable{Showable}{indent} with no content

\endshowable








## Expand all

Typically used when developing content, you can instruct the showable module to invert the show/hide status of all showables 
in a page by adding *?exp* to the url in your browser.

**NOTE**: this presently *toggles all* showable so *Inverted* showables will be shown.  Future version will changed so that this option
will *open all* rather than *toggle all*


**example**:

<a href="?exp">Show</a> all showables in this page.


