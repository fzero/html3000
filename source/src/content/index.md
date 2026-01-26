When Tim Berners-Lee invented HTML his idea was to share documents – scientific papers to be precise. This document shape is still with us after all this time. That's why we have elements like `<article>`, `<aside>`, `<header>`, `<footer>`, `<p>` and so on.

This works great for articles and blogs, but the web has changed. Today the majority of what we build are applications, not documents, and the metaphors of documents don’t always fit application interfaces. Carousels, badges, counters, avatars, alerts – none of these map neatly to `<article>`, `<header>`, or `<p>`. Instead, we’ve been shoehorning them into non-semantic catch-alls: `<div>` and `<span>`.

## Why `<div>`s Are Harmful

`<div>`s are the duct tape of web development. They:

- Hide the true structure of the UI.
- Depend on fragile, bloated class names for meaning.
- Make code unreadable – it takes mental effort to decode what a Tailwind block is actually doing.
- Encourage short-term hacks instead of long-term maintainable patterns.

The irony is that React developers already know this. They write `<Panel>`, `<Button>`, `<Logo>`, `<Nav>` every day in JSX. Those are semantic! But paradoxically, the same community often declares that semantic HTML is "dead."

It most definitely isn't. In fact, semantic HTML is more important than ever.

## HTML in 2025: Underused and Undervalued

The truth is, HTML and CSS in 2025 are more powerful than many developers realize. Features like CSS nesting, attribute selectors, and custom elements give us expressive, declarative tools that work everywhere without JavaScript or build systems. Put together, these practices feel futuristic – like coding in the year 3000! – even though most of them have been around for years.

That’s why I call this approach **HTML3000**.

## The Principles

At its core, HTML3000 is about leaning into semantics and writing HTML that describes _what_ an element is, not just _how it looks_. The key principles are:

- **Use custom HTML tags extensively.** No `<div>` or `<span>`. If you feel you need these tags, take a step back and figure out what you actually mean. Existing semantinc HTML tags should be considered first but the moment you need something new, build it!

- **Favor context and nesting over class soup.** Remember what the “C” in CSS stands for.

- **Use attributes instead of classes as CSS hooks.** Double down on declarative patterns.

- **Start with reusable patterns** and componentize later.

- **JavaScript comes last.** Focus on structure and styling before behavior.

The goal isn’t to throw out modern tooling. HTML3000 plays nicely with ERB, Hotwire, Stimulus, HTMX, React, Vue, Phoenix LiveView, and more. It’s “just HTML” but written differently.

## Wait, Don't I Need Javascript To Do That?

TL;DR: No.

Custom tags have been allowed since HTML5 was released in January of 2008. You can go ahead and type `<my-tag>` on your code and it will behave like a `<span>`.

Any custom tag is by definition not strictly standard HTML – it's _custom_ after all! – but their default behaviour is standardized.

Javascript is only needed if you're implementing interactive behaviours, as usual. Complex elements with all bells and whistles can always be created as [web components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components), but that's not what we're talking about here.

Rest assured these are two separate features: custom HTML tags don't need any Javascript to work. You can simply add them to your code and apply CSS defitions as you would for any other HTML tag.

That's how we're getting rid of `<span>` and `<div>` in favour of fully semantic tags to describe applications UIs.

## Fixing the Tailwind website example

<p
  class="codepen"
  data-height="400"
  data-default-tab="html,result"
  data-slug-hash="JoYLqoP"
  data-pen-title="HTML3000: Fixing the Now Playing Tailwind example"
  data-user="fzero"
  data-editable="true"
  style="
    height: 400px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 2px solid;
    margin: 1em 0;
    padding: 1em;
  "
>
  <span
    >See the Pen
    <a href="https://codepen.io/fzero/pen/JoYLqoP">
      HTML3000: Fixing the Now Playing Tailwind example</a
    >
    by Fabio Neves (<a href="https://codepen.io/fzero">@fzero</a>) on
    <a href="https://codepen.io">CodePen</a>.</span
  >
</p>
<script
  async
  src="https://public.codepenassets.com/embed/index.js"
></script>

## A javascript-free badge component

<p
  class="codepen"
  data-height="400"
  data-default-tab="html,result"
  data-slug-hash="vENRMWB"
  data-pen-title="HTML3000: Badge example"
  data-editable="true"
  data-user="fzero"
  style="
    height: 400px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 2px solid;
    margin: 1em 0;
    padding: 1em;
  "
>
  <span
    >See the Pen
    <a href="https://codepen.io/fzero/pen/vENRMWB">
      HTML3000: Badge example</a
    >
    by Fabio Neves (<a href="https://codepen.io/fzero">@fzero</a>) on
    <a href="https://codepen.io">CodePen</a>.</span
  >
</p>
<script
  async
  src="https://public.codepenassets.com/embed/index.js"
></script>

## What You Gain Without `<div>`s

- **Readable code** – you know what’s on the page without tracing through CSS classes.
- **Maintainability** – meaningful tags are easier to refactor and extend.
- **Consistency** – naming things pushes you to think in component patterns instead of ad hoc markup.
- **Freedom from bloat** – less dependence on utility libraries to patch over missing semantics.

## Why This Matters

Using semantic, declarative markup makes code easier to read, reason about and maintain. Instead of wading through endless utility classes you see the actual structure of your UI. Consistency emerges naturally and you’re nudged toward building standardized, reusable components.

**Is this a design system?** Nope! But any serious application needs consistent UX, and HTML3000 encourages you to think in components from the start.

## Adopting HTML3000 Incrementally

You don’t need to rewrite everything overnight. Even small steps like replacing anonymous `<div>`s with meaningful custom tags can dramatically improve readability. You can go further by experimenting with attribute selectors or phasing out class-heavy patterns where they don’t serve you.

## Further Reading

- [CSS Classes Considered Harmful](https://www.keithcirkel.co.uk/css-classes-considered-harmful) – the article that sparked much of this thinking.
- [Why Semantic HTML Still Matters](https://www.jonoalderson.com/conjecture/why-semantic-html-still-matters) – a reminder of the foundations we’ve drifted from.
- [Just use a button](https://gomakethings.com/just-use-a-button/) - Don't use a `<div>` to do a `<button>`'s job.
- [PicoCSS](https://picocss.com/) – a CSS framework that embraces semantic, class-less markup.


## Looking Ahead

HTML3000 isn’t a framework, library, or package you install. It’s a set of practices that rediscover the expressive power of HTML and CSS – tools that already run everywhere. It’s about writing code for the web that’s semantic, declarative, and future-proof.

If the early web was about documents and the last decade was about JavaScript-driven UIs, perhaps the next step is recognizing that the simplest building blocks – HTML and CSS – already take us surprisingly far.

HTML3000 isn’t just a practice. It’s a promise: **no more meaningless markup.** Because the future of the web shouldn’t be meaningless.
