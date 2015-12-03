# HTML style guide

Most of the rules in this style guide are based on our own experiences with writing maintainable HTML. Some of the sources that inspired us in the past years, and while writing the style guide:

- [Isobar Front-end Code Standards](https://isobar-idev.github.io/code-standards/#html_html)
- [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.xml)
- [Code Guide by @mdo](http://codeguide.co/)
- [Mozilla's Webdev Bootcamp documentation](http://mozweb.readthedocs.org/en/latest/)
- [html5boilerplate.com](https://html5boilerplate.com/)

## Table of Contents

- [Syntax and whitespace](#syntax-and-whitespace)
	- [Write lowercase tags](#write-lowercase-tags)
	- [Use tabs for indentation](#use-tabs-for-indentation)
	- [Use double quotes on attributes](#use-double-quotes-on-attributes)
	- [Properly close void elements](#properly-close-void-elements)
	- [Don't omit optional closing tags](#dont-omit-optional-closing-tags)
	- [Don't omit optional tags](#dont-omit-optional-tags)
- [Naming convention](#naming-convention)
- [Doctype](#doctype)
- [Language](#language)
- [IE Compatibility mode](#ie-compatibility-mode)
- [Character encoding](#character-encoding)
- [Validation](#validation)

## Syntax and whitespace

The following rules apply:

### Write lowercase tags

```html
<!-- bad -->
<P>I am a paragraph!</P>

<!-- good -->
<p>I am a paragraph!</p>
```

### Use tabs for indentation

```html
<!-- bad -->
<div>
∙∙<p>I am a paragraph!</p>
</div>

<!-- good -->
<div>
	<p>I am a paragraph!</p>
</div>
```

### Use double quotes on attributes

```html
<!-- bad -->
<img src='path/to/file.jpg' alt='A beautiful file' />

<!-- good -->
<img src="path/to/file.jpg" alt="A beautiful file" />
```

### Properly close void elements

Yes, even though trailing slashes optional. We just prefure closure, I guess. :)

```html
<!-- bad -->
<img src="path/to/file.jpg" alt="A beautiful file">

<!-- good -->
<img src="path/to/file.jpg" alt="A beautiful file" />
```

### Don't omit optional closing tags

```html
<!-- bad -->
<ul>
	<li>Item 1
	<li>Item 2
	<li>Item 3
</ul>

<!-- good -->
<ul>
	<li>Item 1</li>
	<li>Item 2</li>
	<li>Item 3</li>
</ul>
```

### Don't omit optional tags

```html
<!-- bad -->
<!doctype html>
<title>Saving money, saving bytes</title>
<p>Qed.

<!-- good -->
<!doctype html>
<html>
	<head>
		<title>Spending money, spending bytes</title>
	</head>
	<body>
		<p>Sic.</p>
	</body>
</html>
```

## Naming convention

We use a BEM-like naming convention for the value of `class` attributes. Read the naming section in our [CSS style guide](https://github.com/procurios/CSS#naming-conventions) for more information.

## Doctype

Always include a proper doctype to trigger standards mode. Omitting the doctype [triggers quirks mode](https://developer.mozilla.org/en-US/docs/Quirks_Mode_and_Standards_Mode) and should always be avoided. The HTML5 doctype is simple and easy to remember:

```html
<!doctype html>
```

## Language

Always include the `lang` attribute on the `html` tag. From the HTML5 spec:

> Authors are encouraged to specify a lang attribute on the root html element, giving the document's language. This aids speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use, and so forth.

Read more about the `lang`` attribute [in the spec](http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element).

Please keep in mind that the charset declaration:

- must be included completely [within the first 1024 bytes of the document](https://www.whatwg.org/specs/web-apps/current-work/multipage/semantics.html#charset)
- should be specified as early as possible (before any content that could be controlled by an attacker, such as a `title` element) in order to avoid a potential [encoding-related security issue](https://code.google.com/p/doctype-mirror/wiki/ArticleUtf7) in Internet Explorer

```html
<html lang="en-us">
	<!-- ... -->
</html>
```

## IE Compatibility mode

Internet Explorer supports the use of a document compatibility `meta`` tag to specify what version of IE the page should be rendered as. Unless circumstances require otherwise, it's most useful to instruct IE to use the latest supported mode with edge mode.

For more information, [read this awesome Stack Overflow article](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e).

Keep in mind that the tag for compatibility mode needs to be included [before all other tags](https://msdn.microsoft.com/en-us/library/cc288325.aspx) except for the `title` and the other `meta` tags.

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge" />
```

## Character encoding

Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document (generally UTF-8).

```html
<head>
	<meta charset="UTF-8" />
</head>
```

## Validation

[Valid markup](https://validator.w3.org/) is a goal but not a mandate. However, be aware validation can be an excellent starting place while debugging a Web page — especially if the problems are unusual.