# Twig style guide

Many of our (UI) components use [Twig](http://twig.sensiolabs.org/documentation) to render HTML. Twig templates contain / compile to a mix of PHP, Javascript and HTML, so our style guides for those languages apply to Twig templates as well ([HTML style guide](https://github.com/procurios/HTML), [Javascript style guide](https://github.com/procurios/Javascript)).

The following coding standards are specifically related to Twig.

## Whitespace

### Place one space after the start of a delimiter

The start of a delimiter is `{{`, `{%`, or `{#`.

```twig
{# bad #}
{{foo }}

{# good #}
{{ foo }}
```

### Place one space before the end of a delimiter

The end of a delimiter is `}}`, `%}`, or `#}`.

```twig
{# bad #}
{{ foo}}

{# good #}
{{ foo }}
```

### Place one space before and after operators

This applies to the following:

- Comparison operators: (`==`, `!=`, `<`, `>`, `>=`, `<=`)
- Math operators (`+`, `-`, `/`, `*`, `%`, `//`, `**`)
- Logic operators (`not`, `and`, `or`), `~`, `is`, `in`)
- The ternary operator (`?:`)

```twig
{{ 1 + 2 }}
{{ foo ~ bar }}
{{ true ? true : false }}
```

#### Exceptions

Don't put any spaces (before or after) the operators `|`, `.`, `..`, `[]`.

```twig
{{ foo|upper|lower }}
{{ user.name }}
{{ user[name] }}
{% for i in 1..12 %}
	{# stuff #}
{% endfor %}
```

### Use camelCase when naming variables

```twig
{# bad #}
{% set foo-bar = 'foo' %}
{% set foo_bar = 'foo' %}

{# good #}
{% set fooBar = 'foo' %}
```

### Use tabs for indentation

Use the same indentation as the one used for the target language of the rendered template.

```twig
{# bad #}
{% block foo %}
	{% if foo.bar %}
	<p>Bar!</p>
	{% endif %}
{% endblock %}

{# good #}
{% block foo %}
	{% if foo.bar %}
		<p>Bar!</p>
	{% endif %}
{% endblock %}
```

## Comparison & Equality

### Use shortcuts

```twig
{# bad #}
{% if myArray|length > 0 %}
	{# stuff #}
{% endif %}

{# good #}
{% if myArray %}
	{# stuff #}
{% endif %}
```

## Splitting files

Twig makes it very easy to split discrete chunks of code into their own file. A rule that forces developers to split files into multiple ones doesn't make much sense, but the least the style guide can do is to encourage you to consider it. If it eases readability, maintenance and interoperability: please do so.

```twig
<div class='FooComponent'>
	{% include 'FooComponent__header.html.twig' %}
</div>
```

### Don't use `block` and `extends`

Twig allows defining one or more `block`s in a template. Blocks are used for inheritance and act as placeholders and replacements at the same time.

```twig
{# FooComponent.html.twig #}
<div class='FooComponent'>
	{% block header %}
		{# optional default stuff #}
	{% endblock %}
</div>
```

```twig
{# FooComponent__header.html.twig #}
{% extends 'FooComponent.html.twig' %}
{% block header %}
	{# stuff replacing default stuff #}
{% endblock %}
```

As a rule of thumb: don't use it. It quickly leads to complicated code and invisible dependencies. Instead, compose your component out of multiple smaller files and simply include them.