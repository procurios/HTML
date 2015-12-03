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

### Don't put any spaces before and after the following operators: `|`, `.`, `..`, `[]`

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