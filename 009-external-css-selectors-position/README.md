# External CSS, Selectors and Position

This chapter introduces external CSS files, selectors, and a practical set of CSS properties for styling a complete page.

## Table of Contents

- [Why external CSS files matter](#why-external-css-files-matter)
- [Linking a stylesheet](#linking-a-stylesheet)
- [Selectors](#selectors)
- [Useful starter properties](#useful-starter-properties)
- [Cascade and specificity recap](#cascade-and-specificity-recap)
- [The position property](#the-position-property)
- [Exercise](#exercise)
- [Resources](#resources)

## Why external CSS files matter

External stylesheets help because:

- they keep the HTML cleaner
- they make styles reusable
- they are easier to maintain

Example:

```css
/* styles.css */

body {
  background: #f6ede3;
  color: #3b2f2f;
}

.recipe-card {
  background: #fffdf9;
  max-width: 680px;
  margin: 0 auto;
}
```

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="./styles.css" />
</head>
```

## Linking a stylesheet

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Classic Tiramisu Recipe</title>
  <link rel="stylesheet" href="./styles.css" />
</head>
```

## Selectors

Live example:

- [HTML demo file](./examples/selectors-demo.html)
- [CSS demo file](./examples/selectors-demo.css)

Additional selector examples:

- `:hover` for interactive states
- `:first-child` and `:last-child` for items inside a group
- `::before` and `::after` for generated content
- `::selection` for selected text
- combined selectors like `.combined-demo:hover li:first-child::after`

### Tag selectors

```css
body {
  margin: 0;
  font-family: Georgia, serif;
}

h1 {
  color: #5c3a21;
}
```

Typical use:

- you want a broad rule
- you want to style common HTML elements

### Class selectors

```css
.recipe-card {
  padding: 40px;
  border-radius: 16px;
}

.meta-item {
  display: inline-block;
}
```

Typical use:

- you want reusable styling
- you want precise control
- you are styling components or sections

### ID selectors

```css
#main-title {
  letter-spacing: 0.5px;
}
```

Typical use:

- you need a unique hook
- the element really is unique on the page

### Combined selectors

```css
.tip h2 {
  margin-top: 0;
}

.ingredients li {
  margin-bottom: 8px;
}
```

These selectors can be read as:

- "Select all `li` elements inside `.ingredients`"
- "Select the `h2` inside `.tip`"

## Useful starter properties

These CSS properties are enough to begin styling the page with confidence.

### Text and color

```css
body {
  color: #3b2f2f;
  font-family: Georgia, serif;
  font-size: 16px;
  line-height: 1.6;
}

h1 {
  font-size: 42px;
  font-weight: 700;
}
```

Common uses:

- text color
- readable typography
- hierarchy between headings and body text

### Text formatting demo

Live example:

- [HTML demo file](./examples/text-formatting-demo.html)
- [CSS demo file](./examples/text-formatting-demo.css)

These properties are useful for headings, links, captions, taglines, and small UI details.

### Spacing

Live example:

- [HTML demo file](./examples/box-styling-demo.html)
- [CSS demo file](./examples/box-styling-demo.css)

```css
.recipe-card {
  margin: 40px auto;
  padding: 40px;
}

.steps li {
  margin-bottom: 16px;
}
```

Common uses:

- space outside an element with `margin`
- space inside an element with `padding`

The examples cover `background-color`, `border`, `border-radius`, `padding`, `margin`, `width`, and `max-width`.

### Size

```css
.recipe-card {
  max-width: 680px;
}

.hero-photo {
  width: 100%;
}
```

Common uses:

- limiting line length and content width
- making images responsive inside their container

### Surface styling

```css
.recipe-card {
  background-color: #fffdf9;
  border: 1px solid #eadfce;
  border-radius: 16px;
}
```

Common uses:

- cards
- highlighted sections
- soft visual grouping

## Cascade and specificity recap

The cascade determines which CSS rule is applied when multiple rules can target the same element.

```css
p {
  color: black;
}

.tagline {
  color: #8a7363;
}
```

If both rules target the same paragraph:

- the more specific selector wins
- if specificity is equal, the later rule wins

Rule of thumb:

- inline styles are very strong
- ids are stronger than classes
- classes are stronger than tag selectors

The main idea is understanding why a style may or may not appear on the page.

## The position property

The `position` property is best understood as a small set of behaviors rather than a full layout system.

### Quick demo setup

Live example:

- [HTML demo file](./examples/position-demo.html)
- [CSS demo file](./examples/position-demo.css)

The live example is split into small sections for `static`, `relative`, `absolute`, `sticky`, and `fixed`, so each behavior can be demonstrated separately.

### `position: static`

This is the default.

```css
div {
  position: static;
}
```

- the element stays in the normal flow
- `top`, `right`, `bottom`, `left` do not have effect here

Even when `top` and `left` are written, the box does not move.

### `position: relative`

```css
.badge {
  position: relative;
  top: -4px;
  left: 8px;
}
```

- the element keeps its original space
- it can be shifted visually from its normal position
- often used as the parent for absolutely positioned children

The box moves visually, but its original space still remains in the layout.

### `position: absolute`

```css
.card {
  position: relative;
}

.label {
  position: absolute;
  top: 16px;
  right: 16px;
}
```

- the element is taken out of normal flow
- it positions itself relative to the nearest positioned ancestor
- if there is no positioned ancestor, it may position relative to the page

The badge is absolutely positioned, so it looks for the nearest positioned parent. When `.demo-card` has `position: relative`, the badge stays attached to the card.

The box leaves the normal flow, so the other boxes no longer reserve space for it.

Common examples:

- a small "Easy" badge on the recipe card
- a label on top of the hero image

### `position: fixed`

```css
.back-to-top {
  position: fixed;
  right: 16px;
  bottom: 16px;
}
```

- the element stays attached to the viewport
- good for floating buttons, chat widgets, sticky helpers

The button stays in the same place even while the page scrolls.

### `position: sticky`

```css
.section-title {
  position: sticky;
  top: 0;
  background: white;
}
```

- behaves like a normal element at first
- becomes sticky when scrolling reaches the threshold
- useful for headers, table headings, side navigation

The title scrolls normally at first, then sticks to the top of its scroll container.

Note:

- `position` is not the main tool for page layout
- use Flexbox and Grid for most layout work
- use `position` for overlays, badges, floating UI, and special cases

## Exercise

### Main Exercise: Finish Tiramisu with External CSS in JSFiddle

Start from [the plain tiramisu HTML](../008-css-intro/01-tiramisu-html-only/index.html).

- paste the plain HTML into the HTML panel
- write the CSS in the CSS panel
- add classes where needed
- style the recipe card, image, meta items, ingredients, steps, and footer

Checklist:

- page background color
- readable font and text color
- centered recipe card with spacing
- styled meta badges
- full-width hero image
- spacing between sections
- highlighted chef's tip box

Suggested order:

1. Style the whole page first: `body`, text color, font, background
2. Style the main card: width, spacing, background, rounded corners
3. Style headings and text
4. Style the meta badges
5. Style the image and the tip box

## Resources

- [CSS selectors on MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Basic_selectors)
- [position on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [Specificity on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_cascade/Specificity)
- [Video recordings](https://drive.google.com/drive/folders/19bdFIfuYOfBda2jQYK1Vz63EKUN57rvQ)
- [DEV course website](https://dev-course-phi.vercel.app/)
