# html3000
No `<div>`s, no `<span>`s, no classes, no problem

## HTML and semantics

The web was initially just text, so it made sense to build a language to describe documents.

That's why elements such as `<article>`, `<aside>`, `<header>`, `<footer>`, `<p>` etc. exist: they literally describe what they do.

In other words, they're *semantic*.

> Semantic = saying what you mean

Things evolved pretty quickly though and now we have millions of web applications using HTML to describe the UI.

BUT! Everything that's not document-shaped - e.g. panels, alerts cards, carousels, badges, counters, avatars - is represented by non-semantic catch-all elements like `<div>` and `<span>`.

## What is a `<div>` anyway?

I can tell you what `<main>`, `<article>`, `<nav>`, `<header>` and `<footer>` mean, but what about `<div>`? What does `<div>` mean?

`<div>` is a bucket to throw classes at. The semantics of `<div>` are defined by css classes in frameworks like Bootstrap and Tailwind, aside from defining how it should look. This leads to terrible code like this:

**(Add example of horrible tailwind code here)**

It's impossible to know what this does at first glance! It takes quite a few seconds to parse all the classes and figure out what this is.

## Old man rant

People don't care as much about this because we live in the post-React era. React brought forth the everything-in-JS culture which made most developers forget the basics.

I call it React's Great Front-End Knowledge Apocalypse.

Tailwind is a consequence of this.

Nobody knows CSS anymore and most beginner devs don't even know proper HTML. This results in slow, bloated code that reinvents basic browser functions in JS without any real need.

## Back to it

HTML and CSS are awesome in 2025 and there are a few overlooked features that can completely change how front-end is coded.

I've put together a set of practices and ideas to put those features to good use. It feels like the future even though every single technique works in all browsers – most of features have been around for decades!

I call it **HTML3000**.

## The principles

- Use custom HTML tags extensively. No `<div>`s, no `<span>`s
- Context and nesting > tons of classes
	- Remember what the "C" in CSS means
		- From Codecademy: "Cascading in CSS refers to the way style rules are applied based on a hierarchy, where more specific or later-defined rules override less specific or earlier ones. This allows browsers to determine which styles to apply when multiple rules target the same element."
- Use attributes instead of classes as CSS hooks
	- Double down on declarative!
- Create simple reusable patterns first and web components second
	- Only if you really need them
- JS **always** comes last

### Use custom HTML tags extensively

```html
<div class="card card--rounded card--dropshadow">
  <h3 class="card-title">
    Example card
  </h3>
  <p class="card-body">
    A longer example text that goes with the title
  </p>
</div>
```

```html
<card rounded dropshadow>
  <h3>
    Example card
  </h3>
  <p>
    A longer example text that goes with the title
  </p>
</card>
```

### Context and nesting > tons of classes

```css
card {
  + [rounded] {
    ...
  }

  + [dropshadow] {
    ...
  }

  h3 {
    ...
  }
}
```

A `<h3>` can be defined multiple times in CSS. The top one will be the general look while in the `<body>` and the version defined in `<card>` will be used for all `<h3>` tags inside `<card>`. Design systems are all about consistency so it's desirable to set up these conventions anyway.

### Use attributes instead of classes as CSS hooks

Custom HTML tags make everything much easier to read and reason about, not to mention shorter! To double down on declarative, we can define variations in design or behaviour using attributes instead of classes.

Why? For one, readability. But also, this is the bit that makes React developers realize that you probably don't need JS for most things.

A `<custom-tag>` with controlled with attributes just feels right. It brings precisely the same kind of consistency that a React-based component system does, only without any JS.

### Create simple reusable patterns first, then automate

Using custom tags makes it easier to understand the page structure and avoiding using 10 nested divs for no reason. Nesting will happen, but being able to name elements makes it make sense. It should be pretty obvious why a `<widget>` should be nested within a `<toolbar-group>` within a `<toolbar>` - it tells the whole story right there.

So instead of creating a `<Widget>` React element that spits out a bunch of nested `<div>`s without any interaction, nail the naked code first.

By the way, yes, you can mix HTML3000 and React, nothing wrong about it! But we're talking about Rails here, and I've got good news.

## Examples

- [Fixing the Now Playing widget from Tailwind home](https://codepen.io/fzero/pen/JoYLqoP?editors=1100)
- [Badges](https://codepen.io/fzero/pen/vENRMWB?editors=1100)

## On a Rails/ERB context

HTML3000 works great with ERB, Hotwire and Stimulus since we're not really doing anything special – it's just HTML after all. In
fact `<turbo-frame>` is itself web component using a custom tag.

(Incidentally web components – or more accurately custom HTML components – is something everyone should know more about.)

HTML3000 is not about web components, but there's definitely a philosophical overlap.

## References

- [CSS classes considered harmful](https://www.keithcirkel.co.uk/css-classes-considered-harmful/)
- [Why semantic HTML still matters](https://www.jonoalderson.com/conjecture/why-semantic-html-still-matters/)
- [PicoCSS](https://picocss.com)
