# Flexbox and Grid

This chapter introduces the two most important modern CSS layout systems:

- `Flexbox` for one-dimensional layout
- `Grid` for two-dimensional layout

For designers working in Figma, Flexbox is very close to Auto Layout. Grid is closer to page structure, layout grids, galleries, and dashboards.

## Table of Contents

- [Flexbox and Figma](#flexbox-and-figma)
- [Grid and page structure](#grid-and-page-structure)
- [Flexbox examples](#flexbox-examples)
- [Grid examples](#grid-examples)
- [Flexbox practice](#flexbox-practice)
- [Grid practice](#grid-practice)
- [Resources](#resources)

## Flexbox and Figma

Flexbox is used when items should be arranged in one direction:

- left to right
- top to bottom

This is very similar to **Auto Layout** in Figma.

How this maps to Figma:

- `display: flex` = turn the parent into an Auto Layout container
- `flex-direction: row` = horizontal Auto Layout
- `flex-direction: column` = vertical Auto Layout
- `gap` = spacing between items
- `justify-content` = distribution on the main axis
- `align-items` = alignment on the cross axis
- `flex-wrap` = wrap items onto a new line
- `flex-grow` = allow an item to take available space

## Grid and page structure

Grid is used when both rows and columns matter at the same time.

Grid is useful for:

- page sections
- card galleries
- dashboards
- magazine-like layouts
- layouts with items that span multiple columns or rows

How this relates to page structure in Figma:

- `display: grid` = turn the parent into a grid container
- `grid-template-columns` = define the columns
- `grid-template-rows` = define the rows
- `gap` = spacing between tracks
- `grid-column` = control horizontal placement and column span
- `grid-row` = control vertical placement and row span
- `span` is used inside `grid-column` or `grid-row`, for example `grid-column: span 2;`

Different ways to define columns:

```css
grid-template-columns: 200px 200px 200px;
grid-template-columns: 20% 40% 40%;
grid-template-columns: 1fr 1fr 1fr;
grid-template-columns: 240px 1fr;
grid-template-columns: repeat(3, 1fr);
grid-template-columns: repeat(4, minmax(120px, 1fr));
```

## Flexbox examples

Live example:

- [HTML demo file](./examples/flexbox-demo.html)
- [CSS demo file](./examples/flexbox-demo.css)

## Grid examples

Live example:

- [HTML demo file](./examples/grid-demo.html)
- [CSS demo file](./examples/grid-demo.css)

## Flexbox practice

Practice game:

- [Flexbox Froggy](https://flexboxfroggy.com/)

## Grid practice

Practice game:

- [Grid Garden](https://cssgridgarden.com/)

## Resources

- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Basic concepts of flexbox on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)
- [Basic concepts of grid layout on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout)
- [Flexbox Froggy](https://flexboxfroggy.com/)
- [Grid Garden](https://cssgridgarden.com/)
- [Video recordings](https://drive.google.com/drive/folders/19bdFIfuYOfBda2jQYK1Vz63EKUN57rvQ)
- [DEV course website](https://dev-course-phi.vercel.app/)
