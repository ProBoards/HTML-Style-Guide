# HTML Style Guide
The ProBoards Official HTML Style Guide

The purpose of this document is to provide guidelines for writing HTML. Code conventions are important for the long-term maintainability of code. Most of the time, developers are maintaining code, either their own or someone else's. The goal is to have everyone’s code look the same, which allows any developer to easily work on another developer’s code.

We've used the following resources as a base from which to build:
- [Google's HTML Guide](https://google.github.io/styleguide/htmlcssguide.xml)
- [Code Guide by @mdo](http://codeguide.co/#html)
- [Primer Guidelines](http://primercss.io/guidelines)
- [w3schools HTML5 Style Guide and Coding Conventions](http://www.w3schools.com/html/html5_syntax.asp)

## Formatting

#### Capitalization

Lowercase all tags, attributes, and attribute values, with the exception of `text/CDATA` and strings.

```html
<!-- bad -->
<SPAN CLASS="TEST">Test</SPAN>

<!-- good -->
<span class="test">Test</span>
```

#### Spaces or Tabs?

Each indentation level is made up of four spaces. Do not use tabs. (Please set your editor to use four spaces)

```html
<!-- bad -->
<ul>
  <li>Fantastic
  <li>Great
</ul>

<!-- bad -->
<ul>
	<li>Fantastic
	<li>Great
</ul>

<!-- good -->
<ul>
    <li>Fantastic
    <li>Great
</ul>
```

#### Linebreaks

Use Unix-style line endings ('\n') rather than Windows-style ('\r\n').

#### Whitespace

Remove unecessary whitespace, both in the form of trailing whitespace characters and extra blank lines, as they can complicate diffs.  Blank lines may be used to separate non-related elements, but related elements should not include extra lines.

```html
<!-- bad -->
<body>     

    <h1>Headline!</h1>     

    <h2>Subtitle</h2>     

    <div>     
        Content goes here.     
    </div>     

</body>     

<!-- good -->
<body>
    <h1>Headline!</h1>

    <h2>Subtitle</h2>
    <div>
  	  Content goes here.
    </div>
</body>
```

#### Indentation

Use a new line for every block, list, or table element, and indent every such child element.  If you run into issues around whitespace between list items it’s acceptable to put all `li` elements in one line.

```html
<!-- TODO: expand examples here -->
<blockquote>
    <p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
    <li>Moe
    <li>Larry
    <li>Curly
</ul>
```


## General

#### HTML Validity

Use valid HTML code unless that is not possible due to otherwise unattainable performance goals regarding file size.  Use tools such as the [W3C HTML validator](https://validator.w3.org/nu/) to test.  Using valid HTML is a measurable baseline quality attribute that contributes to learning about technical requirements and constraints, and that ensures proper HTML usage.

#### Separation of Concerns

Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.  That is, make sure documents and templates contain only HTML and HTML that is solely serving structural purposes. Move everything presentational into style sheets, and everything behavioral into scripts.  In addition, keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.  Separating structure from presentation from behavior is important for maintenance reasons. It is always more expensive to change HTML documents and templates than it is to update style sheets and scripts.

```html
<!-- bad -->
<head>
    <title>HTML sucks</title>
    <link rel="stylesheet" href="base.css" media="screen">
    <link rel="stylesheet" href="grid.css" media="screen">
    <link rel="stylesheet" href="print.css" media="print">
</head>
<body>
    <h1 style="font-size: 1em;">HTML sucks</h1>
    <p>
    	I’ve read about this on a few sites but now I’m sure:
        <u>HTML is stupid!!1</u>
        <center>I can’t believe there’s no way to control the styling of
        my website without doing everything all over again!</center>
    </p>
  
<!-- good -->
<head>
    <title>My first CSS-only redesign</title>
    <link rel="stylesheet" href="default.css">
</head>
<body>
	<h1>My first CSS-only redesign</h1>
	<p>
	    I’ve read about this on a few sites but today I’m actually
	    doing it: separating concerns and avoiding anything in the HTML of
	    my website that is presentational.
	</p>
```

#### JavaScript Generated Markup

Writing HTML markup in a JavaScript file makes the content harder to find, harder to edit, and less performant. Avoid it whenever possible.

#### Semantics

Use HTML elements according to their intended purpose.  For example, use heading elements for headings, `p` elements for paragraphs, `a` elements for anchors, etc.  Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

```html
<!-- bad -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- good -->
<a href="recommendations/">All recommendations</a>
```

#### Optional Tags (Optional)

Omit optional tags.  For file size optimization and scannability purposes, consider omitting optional tags. The [HTML5 specification](https://whatwg.org/specs/web-apps/current-work/multipage/syntax.html#syntax-tag-omission) defines what tags can be omitted.  *This approach may require a grace period to be established as a wider guideline as it’s significantly different from what web developers are typically taught. For consistency and simplicity reasons it’s best served omitting all optional tags, not just a selection.*

```html
<!-- bad -->
<!DOCTYPE html>
<html>
  <head>
    <title>Spending money, spending bytes</title>
  </head>
  <body>
    <p>Sic.</p>
  </body>
</html>

<!-- good -->
<!DOCTYPE html>
<title>Saving money, saving bytes</title>
<p>Qed.
```

#### Avoid Superfluous Parent Elements

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML.

```html
<!-- bad -->
<span class="avatar">
  <img src="...">
</span>

<!-- good -->
<img class="avatar" src="...">
```

#### Comments

Use comments to explain code in terms of what it covers, what purposes it serves, and why this solution was used or preferred.  It is not deemed a realistic expectation to always demand fully documented code. Mileage may vary heavily for HTML code and depends on the project’s complexity.  Short comments should be written on one line, with a space after `<!--` and a space before `-->`.  Long comments spanning many lines should be written with `<!--` and `-->` on separate lines.  Never use comments to mark closing tags.


```html
<!-- bad -->
<!--This is a comment-->
<!-- 
	This is a comment
-->
<!-- This is a long comment example. This is a long comment example. This is a long comment example.
  This is a long comment example. This is a long comment example. This is a long comment example. -->
<!-- /.element -->

<!-- good -->
<!-- This is a comment -->
<!-- 
  This is a long comment example. This is a long comment example. This is a long comment example.
  This is a long comment example. This is a long comment example. This is a long comment example.
-->
```
#### Todos

Mark todos and action items with a TODO.  Highlight todos by using the keyword TODO only, followed by a colon.

```html
<!-- TODO: Add bananas -->
<ul>
    <li>Apples</li>
    <li>Oranges</li>
</ul>
```

#### Resource Protocols

Omit the protocol portion (http:, https:) from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.  Omitting the protocol makes the URL relative which prevents mixed content issues and results in minor file size savings.

```html
<!-- bad -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
<script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- good -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

#### Attributes (spaces and equals signs/html quotation marks/no value for boolean attrs)

Omitting spaces around equal signs makes attributes easier to read and groups entities together better.  When quoting attributes values, use double quotation marks ("") rather than single quotation marks ('') around attribute values.  Many attributes don’t require a value to be set, like disabled or checked, so don’t set them.  For more information, read the [WhatWG section](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes).

```html
<!-- bad -->
<a class='something' id='somethingelse'>Button</a>
<a class = "something" id = "somethingelse">Button</a>
<input type="text" disabled="disabled">


<!-- good -->
<a class="something" id="somethingelse">Button</a>
<input type="text" disabled>
```


## Head

#### Document Type

Use HTML5 (HTML syntax) for all HTML documents.  It’s recommended to use HTML, as text/html. Do not use XHTML. XHTML, as application/xhtml+xml, lacks both browser and infrastructure support and offers less room for optimization than HTML.  The word doctype should be lowercase, to maintain consistency with other tags.

```html
<!doctype html>
```

#### Language Attribute

The HTML element should declare the language of the overall page.  This may need to be more dynamic with the introduction of i18n, and an eye should be kept on it

```html
<html lang="en-US">
```

#### Document Encoding

Make sure your editor uses UTF-8 as character encoding, without a byte order mark.  Specify the encoding in HTML templates and documents via the charset attribute of the meta tag.  This tag should be the first element in the head, as some browsers will only read the first 1024 bytes when looking for what charset to apply, and not having one defined can result in vulnerabilities to some cross-scripting techniques.

```html
<head>
    <meta charset="utf-8">
```

#### Viewport Scaling

The head should contain a meta viewport tag to ensure proper display of a page on mobile devices.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

#### Title Tag

Every page must have a title tag, with a well thought out title, since this element will show up as the page title as well as usually being the name of the page when viewed from a search engine.

```html
<title>The Title of the Page</title>
```

#### Meta Description

The meta description tag should be used where feasible to provide a short description of the page.  In some situations search engines will use this description as part of the snippet shown in search results.

```html
<meta name="description" content="A description of the page">
```

#### Other Meta Tags

Meta tags other than the ones already specified here are, as a rule, not necessary.  There should no longer be a reason to include other meta tags that we have in the past.  The only exceptions to this are the OpenGraph and similar tags used for social sharing.

```html
<!-- bad -->
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

#### `type` Attributes

Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).  Specifying type attributes in these contexts is not necessary as HTML5 implies `text/css` and `text/javascript` as defaults. This can be safely done even for older browsers.

```html
<!-- bad -->
<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">
<script src="//www.google.com/js/gweb/analytics/autotrack.js" type="text/javascript"></script>
  
<!-- good -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

## Body

#### Header Tags

Every page should properly utilize appropriate header tags (`h1` to `h6`) to designate sections of the page.  Correct use of these tags will enhance the usability and searchability of pages.

```html
<body>
    <h1>Page Title</h1>

    <h2>Section One</h2>
    <p>...</p>

    <h2>Section Two</h2>
    <p>...</p>
```

#### Tables

Make use of <thead>, <tfoot>, <tbody>, and <th> tags (and scope attribute) when appropriate. Note that <tfoot> goes above <tbody> for speed reasons. You want the browser to load the footer before a table full of data.  **Never use a table for layout purposes**.

```html
<table summary="This is a chart of invoices for 2011.">
    <thead>
        <tr>
            <th scope="col">Table header 1</th>
            <th scope="col">Table header 2</th>
        </tr>
    </thead>
    <tfoot>
        <tr>
            <td>Table footer 1</td>
            <td>Table footer 2</td>
        </tr>
    </tfoot>
    <tbody>
        <tr>
            <td>Table data 1</td>
            <td>Table data 2</td>
        </tr>
    </tbody>
</table>
```

#### Form Inputs (every form input with text should use label)

Wrap inputs and their text in `<label>`s. No need for `for` attributes here, the wrapping automatically associates the two.

```html
<!-- bad -->
<label for="username">Click me</label>
<input type="text" id="username">

<!-- good -->
<label>
    Click me <input type="text" id="username">
</label>
```

#### Form Buttons (form buttons should have explicit types/primary form button should come first)

Form buttons should always include an explicit type. Use primary buttons for the type="submit" button and regular buttons for type="button".  The primary form button must come first in the DOM, especially for forms with multiple submit buttons. The visual order should be preserved with float: right; on each button.

```html
<!-- bad -->
<input value="Click me">
<input type="button" value="Submit Form">

<!-- good -->
<input type="submit" value="Submit Form">
<input type="button" value="Click me">
```

#### `<br>` Tags

`br` tags should not be used as visual spacers, they should only be used to break lines.  There should never be more than one `br` at a time.

```html
<!-- bad -->
</p><br><br>

  
<!-- good -->
</p><br>
```

#### List Elements

Items in list form should always be in `ul`, `ol`, or `dl` tags. Never use a set of `div` or `p` tags.

```html
<!-- bad -->
<div class="list-item">item 1</div>
<div class="list-item">item 2</div>
<div class="list-item">item 3</div>

<!-- good -->
<ul>
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
</ul>
```

#### Entity References

Do not use entity references.  There is no need to use entity references like `&mdash;`, `&rdquo;`, or `&#x263a;`, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.  The only exceptions apply to characters with special meaning in HTML (like < and &) as well as control or "invisible" characters like non-breaking spaces.

```html
<!-- bad -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

<!-- good -->
The currency symbol for the Euro is “€”.
```

#### Multimedia Fallbacks

For multimedia, such as images, videos, and animated objects via canvas, make sure to offer alternative access. For images that means use meaningful alternative text (alt) and for video and audio transcripts and captions, if available.  Providing alternative contents is important for accessibility reasons: A blind user has few cues to tell what an image is about without @alt, and other users may have no way of understanding what video or audio contents are about either.  For images whose alt attributes would introduce redundancy, and for images whose purpose is purely decorative which you cannot immediately use CSS for, use no alternative text, as in alt="".

```html
<!-- bad -->
<img src="spreadsheet.png">

<!-- good -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot">
```
