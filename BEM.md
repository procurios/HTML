# BEM-like naming convention

> There are only two hard things in Computer Science: cache invalidation and naming things.
>
> -- Phil Karlton

We've had numerous naming conventions aiming for consistent naming across developers. It's hard.

Meet BEM. BEM, meaning _Block_, _Element_, _Modifier_, is a front-end methodology [coined by developers working at Yandex](https://tech.yandex.com/bem/). Whilst BEM is a complete methodology, here we are only concerned with its naming convention. Further, the naming convention here only is BEM-like; the principles are exactly the same, but the actual syntax differs slightly and is adopted [from Harry Roberts guidelines](http://cssguidelin.es/#bem-like-naming).

It is a very smart way of naming your CSS classes to give them more transparency and meaning to other developers. They are far more strict and informative, which makes the BEM naming convention _ideal for teams of developers on larger projects_ that might last a while. In other words: it exactly fits our needs at Procurios. It isn't a silver bullet, but sometimes feels like one.

BEM splits classes into three groups:

- `Block`: The sole root of the component.
- `Element`: Represents a descendent of `Block` that helps form `Block` as a whole.
- `Modifier`: A variant, different state or extension of the `Block`.

To take an analogy (examples are CSS, obviously using the value of HTML class attributes):

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

Harry Roberts wrote [a great article explaining the BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/). Some quotes:

> The point of BEM is to tell other developers more about what a piece of markup is doing from its name alone. By reading some HTML with some classes in, you can see how – if at all – the chunks are related; something might just be a component, something might be a child, or element, of that component, and something might be a variation or modifier of that component. To use an analogy/model, think how the following things and elements are related:

```css
.person {}
.person__hand {}
.person--female {}
.person--female__hand {}
.person__hand--left {}
```

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
.Menu-isHidden {}
```

## BEMIT

Harry Roberts has extended the BEM naming convention with namespaces and responsive suffixes. We don't use those concepts (yet), simply because we have no need to. Namespaces aren't an issue, as our platform focuses on independent, isolated and reusable Components. We solve responsiveness with element queries (read more about those in [our CSS style guide](https://github.com/procurios/CSS)).