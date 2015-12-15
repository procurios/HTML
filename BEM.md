# BEM-like naming convention

> There are only two hard things in Computer Science: cache invalidation and naming things.
>
> -- Phil Karlton

We've had numerous naming conventions aiming for consistent naming across developers. It's hard.

## BEM

Meet BEM. BEM, meaning _Block_, _Element_, _Modifier_, is a front-end methodology [coined by developers working at Yandex](https://tech.yandex.com/bem/). Whilst BEM is a complete methodology, here we are only concerned with its naming convention. Further, the naming convention here only is BEM-like; the principles are exactly the same, but the actual syntax differs slightly and is adopted [from Harry Roberts guidelines](http://cssguidelin.es/#bem-like-naming).

It is a very smart way of naming your CSS classes to give them more transparency and meaning to other developers. They are far more strict and informative, which makes the BEM naming convention _ideal for teams of developers on larger projects_ that might last a while. In other words: it exactly fits our needs at Procurios. It isn't a silver bullet, but sometimes feels like one.

BEM splits classes into three groups:

- `Block`: The sole root of the component.
- `Element`: Represents a descendent of `Block` that helps form `Block` as a whole.
- `Modifier`: A variant, different state or extension of the `Block`.

To take an analogy (examples are CSS, but this obviously applies to HTML as well):

```css
.person {
	...
}

.person__head {
	...
}

.person__head--small {
	...
}

.person__head--large {
	...
}

.person--tall {
	...
}
```

Harry Roberts wrote [a great article explaining the BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/). A quote:

> The point of BEM is to tell other developers more about what a piece of markup is doing from its name alone. By reading some HTML with some classes in, you can see how – if at all – the chunks are related; something might just be a component, something might be a child, or element, of that component, and something might be a variation or modifier of that component. Think how the following things and elements are related:

```css
.person {}
.person__hand {}
.person--female {}
.person--female__hand {}
.person__hand--left {}
```

### BEMIT

Harry Roberts has extended the BEM naming convention with namespaces and responsive suffixes. We don't use those concepts (yet), simply because we have no need to. Namespaces aren't an issue, as our platform focuses on independent, isolated and reusable Components. We solve responsiveness with element queries (read more about those in [our CSS style guide](https://github.com/procurios/CSS)).

## Text cases

### Use **camelCase** to name your classes

```html
<!-- bad -->
<div class='foo-bar'></div>
<div class='foo_bar'></div>
<div class='foo_bar--Baz'></div>
<div class='foo_bar--baz'></div>
<div class='FOOBAR'></div>

<!-- good -->
<div class='fooBar'></div>
<div class='fooBar__baz'></div>
<div class='fooBar__bazQux'></div>
<div class='fooBar--baz'></div>
<div class='fooBar--bazQux'></div>
<div class='fooBar__bazQux--quux'></div>
<div class='fooBar__bazQux--quuxCorge'></div>
```

### Use **PascalCase** to name the `Block` of a `Component`

At Procurios isolated web components are conveniently named... `Component`. Mind the capital `C`. Use PascalCase to name the root `Block` of a the Component.

```html
<!-- bad -->
<div class='fooComponent'></div>
<div class='foo-component'></div>
<div class='foo_component'></div>

<!-- good -->
<div class='FooComponent'></div>
```

## Syntax

### Delimit `Element`s with two underscores

```css
/** bad */
.FooComponent-footer {
	...
}

.fooComponentFooter {
	...
}

/** good */
.FooComponent__footer {
	...
}
```

[↑ back to top](#table-of-contents)

### Delimit `Modifier`s with two hyphens

```css
/** bad */
.FooComponent-collapsed {
	...
}

.collapsedFooComponent {
	...
}

/** good */
.FooComponent--collapsed {
	...
}
```

[↑ back to top](#table-of-contents)

## States

Use `is-` or `has-` as suffix for states.

```css
/** bad */
.Panel--collapsed {}
.Panel--collapsing {}
.Menu--hidden {}

/** good */
.Panel--isCollapsed {}
.Panel--isCollapsing {}
.Menu--isHidden {}
```

## File names

Our goal is to move all output of our platform to self-contained, isolated Components. A typical file structure of a Component:

```
/FooComponent
	/themes
		/1
			/FooComponent.html.twig
			/FooComponent.css
			/FooComponent.js
```

Please note that all root files have the name of the Component. If you split code into multiple files, use BEM in file names aswell:

```
/FooComponent
	/themes
		/1
			/partials
				FooComponent__bar.html.twig
				FooComponent__baz.html.twig
			/css
				FooComponent.css
				FooComponent__bar.css
				FooComponent__baz.css
			/FooComponent.html.twig
```

BEM works great as a model to name your files in any context. Apply the same file naming pattern if you (are unlucky enough to) work outside the context of a Component. Consistent naming rocks!