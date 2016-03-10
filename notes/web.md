The Web, HTML, Servlets, and Sockets
====================================

# HTML
The [Hypertext Markup Language (HTML)](http://www.w3schools.com/html/html_intro.asp) is the language used to create web pages. It allows a programmer to specify how text should be displayed in the browser using **tags**. Tags specify formatting instructions such as display some text in bold, some text in italics, and some text centered.

```html
<html>
	<head>	
      <title>Sample Page</title>
    </head>
    <body>
    	<h1>This is a test page</h1>
    	<p>This is some <b>bold</b> text...and some <i>italic</i> text.</p>
    	<p>You can also have a <a href="http://www.cs.usfca.edu">link</a>.</p>
    	<hr/>
   </body>
</html>
```

Tags come in pairs. Start tags begin a block and end tags (starting with a forward slash) end a block. Everything from a start to an end tag forms an **element**. Some elements are empty (`<hr/>`). Valid tag names, for example `h1` and `p`, are defined by the HTML standard.

- `h1`...`h6` are heading tags
- `p` specifies a paragraph
- `a` tags can be used to specify links

Images may be included in a page using an `img` tag as below:

```
<img src="http://www.cs.usfca.edu/pic.jpg/> 
```

Comments are specified as below and are ignored when a page is displayed.

```
<!-- This is a comment. -->
```

Ordered (`ol`) and unordered (`ul`) lists are specified as follows:

```
<ul> 
    <li>...</li> <!-- each list item -->
</ul>
```

Tables are also quite useful:

```
<table border="1">	<tr>
		<td>row 1, cell 1</td>
		<td>row 1, cell 2</td>
	</tr>	<tr>
		<td>row 2, cell 1</td>
		<td>row 2, cell 2</td>
	</tr>
</table> 
```

Links are defined with the `a` tag.

```	
<a href="http://www.cs.usfca.edu">link</a>
```

This example opens the link in a new browser tab:

```
<a target=“_blank” href="http://www.cs.usfca.edu">link</a>
```

`href` and `target` are **attributes**, just as `border` is an attribute in the `table` element above. Attributes may be reordered.

```
<a href="http://www.cs.usfca.edu" target=“_blank” >link</a>
```

`script` elements allow you to specify [javascript](http://www.w3schools.com/js/) on your page. 

```
<script type="text/javascript">
	document.write("Hello World!")
</script> 
```

`style` elements allow you to specify inline [cascading style sheets](http://www.w3schools.com/html/html_css.asp), or inline styling information.

```		
<style>
  body {background-color:lightgray}
  h1   {color:blue}
  p    {color:green}
</style>
```

Finally, special characters, like the &, need to be escaped.

```
<p>CS 212 &amp; CS 245 are great classes!</p>
```



