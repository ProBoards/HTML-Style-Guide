# HTML Style Guide
The ProBoards Official HTML Style Guide

The purpose of this document is to provide guidelines for writing HTML. Code conventions are important for the long-term maintainability of code. Most of the time, developers are maintaining code, either their own or someone else’s. The goal is to have everyone’s code look the same, which allows any developer to easily work on another developer’s code.

We've used [Google's HTML Guide](https://google.github.io/styleguide/htmlcssguide.xml) as a base from which to build.

### Protocol

Omit the protocol portion (http:, https:) from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.  Omitting the protocol—which makes the URL relative—prevents mixed content issues and results in minor file size savings.

```html
<!-- Not recommended -->
<script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

### Indentation

Each indentation level is made up of four spaces. Do not use tabs. (Please set your editor to use four spaces)

```html
<!-- Not recommended -->
<ul>
  <li>Fantastic
  <li>Great
</ul>

<!-- Recommended -->
<ul>
    <li>Fantastic
    <li>Great
</ul>
```

### Capitalization

All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA and with the exception of strings).

```html
<!-- Not recommended -->
<A HREF="/">Home</A>

<!-- Recommended -->
<img src="google.png" alt="Google">
```

### Trailing Whitespace

Remove trailing white spaces, as they are unnecessary and can complicate diffs.

```html
<!-- Not recommended -->
<p>What?_

<!-- Recommended -->
<p>Yes please.
```

### Encoding

Make sure your editor uses UTF-8 as character encoding, without a byte order mark.  Specify the encoding in HTML templates and documents via the charset attribute of the meta tag.  More on encodings and when and how to specify them can be found in [Handling character encodings in HTML and CSS](https://www.w3.org/International/tutorials/tutorial-char-enc/).

```html
<meta charset="utf-8">
```

### Comments

Use comments to explain code: What does it cover, what purpose does it serve, why is respective solution used or preferred?

(This item is optional as it is not deemed a realistic expectation to always demand fully documented code. Mileage may vary heavily for HTML and CSS code and depends on the project’s complexity.)

### Action Items

Mark todos and action items with TODO.  Highlight todos by using the keyword TODO only, followed by a colon.

```html
<!-- TODO: remove optional tags -->
<ul>
    <li>Apples</li>
    <li>Oranges</li>
</ul>
```

### Document Type

HTML5 (HTML syntax) is preferred for all HTML documents.  It’s recommended to use HTML, as text/html. Do not use XHTML. XHTML, as application/xhtml+xml, lacks both browser and infrastructure support and offers less room for optimization than HTML.

```html
<!DOCTYPE html>
```

### Void Elements

Although fine with HTML, do not close void elements.  The current list of void elements is area, base, br, col, command, embed, hr, img, input, keygen, link, meta, param, source, track, and wbr.

```html
<!-- Not recommended -->
<br />

<!-- Recommended -->
<br>
```

### HTML Validity

Use valid HTML code unless that is not possible due to otherwise unattainable performance goals regarding file size.  Use tools such as the [W3C HTML validator](https://validator.w3.org/nu/) to test.  Using valid HTML is a measurable baseline quality attribute that contributes to learning about technical requirements and constraints, and that ensures proper HTML usage.

```html
<!-- Not recommended -->
<title>Test</title>
<article>This is only a test.

<!-- Recommended -->
<!DOCTYPE html>
<meta charset="utf-8">
<title>Test</title>
<article>This is only a test.</article>
```

### Semantics

Use HTML according to its purpose.
Use elements for what they have been created for. For example, use heading elements for headings, p elements for paragraphs, a elements for anchors, etc.  Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

```html
<!-- Not recommended -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- Recommended -->
<a href="recommendations/">All recommendations</a>
```

### Multimedia Fallback

For multimedia, such as images, videos, animated objects via canvas, make sure to offer alternative access. For images that means use of meaningful alternative text (alt) and for video and audio transcripts and captions, if available.  Providing alternative contents is important for accessibility reasons: A blind user has few cues to tell what an image is about without @alt, and other users may have no way of understanding what video or audio contents are about either.  For images whose alt attributes would introduce redundancy, and for images whose purpose is purely decorative which you cannot immediately use CSS for, use no alternative text, as in alt="".

```html
<!-- Not recommended -->
<img src="spreadsheet.png">

<!-- Recommended -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

### Separation of Concerns

Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.  That is, make sure documents and templates contain only HTML and HTML that is solely serving structural purposes. Move everything presentational into style sheets, and everything behavioral into scripts.  In addition, keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.  Separating structure from presentation from behavior is important for maintenance reasons. It is always more expensive to change HTML documents and templates than it is to update style sheets and scripts.

```html
<!-- Not recommended -->
<!DOCTYPE html>
<title>HTML sucks</title>
<link rel="stylesheet" href="base.css" media="screen">
<link rel="stylesheet" href="grid.css" media="screen">
<link rel="stylesheet" href="print.css" media="print">
<h1 style="font-size: 1em;">HTML sucks</h1>
<p>I’ve read about this on a few sites but now I’m sure:
  <u>HTML is stupid!!1</u>
<center>I can’t believe there’s no way to control the styling of
  my website without doing everything all over again!</center>
  
<!-- Recommended -->
<!DOCTYPE html>
<title>My first CSS-only redesign</title>
<link rel="stylesheet" href="default.css">
<h1>My first CSS-only redesign</h1>
<p>I’ve read about this on a few sites but today I’m actually
  doing it: separating concerns and avoiding anything in the HTML of
  my website that is presentational.
<p>It’s awesome!
```

### Entity References

Do not use entity references.  There is no need to use entity references like `&mdash;`, `&rdquo;`, or `&#x263a;`, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.  The only exceptions apply to characters with special meaning in HTML (like < and &) as well as control or “invisible” characters (like no-break spaces).

```html
<!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

<!-- Recommended -->
The currency symbol for the Euro is “€”.
```

### Optional Tags

Omit optional tags (optional).  For file size optimization and scannability purposes, consider omitting optional tags. The [HTML5 specification](https://whatwg.org/specs/web-apps/current-work/multipage/syntax.html#syntax-tag-omission) defines what tags can be omitted.  *This approach may require a grace period to be established as a wider guideline as it’s significantly different from what web developers are typically taught. For consistency and simplicity reasons it’s best served omitting all optional tags, not just a selection.*

```html
<!-- Not recommended -->
<!DOCTYPE html>
<html>
  <head>
    <title>Spending money, spending bytes</title>
  </head>
  <body>
    <p>Sic.</p>
  </body>
</html>

<!-- Recommended -->
<!DOCTYPE html>
<title>Saving money, saving bytes</title>
<p>Qed.
```

### type Attributes

Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).  Specifying type attributes in these contexts is not necessary as HTML5 implies text/css and text/javascript as defaults. This can be safely done even for older browsers.

```html
<!-- Not recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">
  
<!-- Recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">

<!-- Not recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js" type="text/javascript"></script>
  
<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

### General Formatting

Use a new line for every block, list, or table element, and indent every such child element.  Indent them if they are child elements of a block, list, or table element.  If you run into issues around whitespace between list items it’s acceptable to put all `li` elements in one line.

```html
<blockquote>
  <p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
  <li>Moe
  <li>Larry
  <li>Curly
</ul>

<table>
  <thead>
    <tr>
      <th scope="col">Income
      <th scope="col">Taxes
  <tbody>
    <tr>
      <td>$ 5.00
      <td>$ 4.50
</table>
```

### HTML Quotation Marks

When quoting attributes values, use double quotation marks ("") rather than single quotation marks ('') around attribute values.

```html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>

<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```
