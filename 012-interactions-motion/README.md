# Interaction States and Motion

This chapter introduces interaction states and motion from a designer's point of view.

The goal is not to memorize CSS syntax. The goal is to understand:

- what state changes exist
- how to describe them clearly to an AI agent

## Table of Contents

- [The four states in this lesson](#the-four-states-in-this-lesson)
- [Hover](#hover)
- [Active](#active)
- [Focus](#focus)
- [Transitions](#transitions)
- [Keyframe animations](#keyframe-animations)
- [How to brief an AI agent](#how-to-brief-an-ai-agent)
- [Quality checklist](#quality-checklist)
- [Examples](#examples)
- [Exercise](#exercise)
- [Resources](#resources)

## The four states in this lesson

### Default

The normal resting state.

This is what the user sees before interacting with the element.

### Hover `:hover`

The pointer is over the element.

Use hover to show that something can be clicked, opened, selected, dragged, or inspected.

### Active `:active`

The element is currently being pressed.

Use active to give a small physical response: a button compresses, a card feels selected, or a control acknowledges the click.

### Focus `:focus`

The element is selected by keyboard navigation or programmatic focus.

Focus is not decoration. It is accessibility feedback. A keyboard user must always be able to see where they are.

## Hover

CSS example:

```css
.button:hover {
  background-color: #2638d9;
  transform: translateY(-2px);
}
```

Design intent:

- make interactivity visible
- add confidence before the click
- keep the change subtle enough that the layout does not jump

## Active

CSS example:

```css
.button:active {
  transform: translateY(1px) scale(0.98);
}
```

Design intent:

- confirm that the press was registered
- make the control feel tactile
- keep the state very short

Active states usually happen while the mouse or finger is down.

## Focus

CSS example:

```css
.button:focus-visible {
  outline: 3px solid #f6b73c;
  outline-offset: 4px;
}
```

Design intent:

- show keyboard users exactly where they are
- make interactive controls usable without a mouse
- keep focus visible on buttons, links, inputs, selects, and custom controls

Use `:focus-visible` when you want the focus ring to appear mainly for keyboard navigation.

Avoid:

```css
*:focus {
  outline: none;
}
```

Removing focus outlines without replacing them is an accessibility bug.

## Transitions

Transitions describe how a property changes between two states.

```css
.button {
  transition: background-color 160ms ease, transform 160ms ease, box-shadow 160ms ease;
}
```

The same idea can be written in a longer form:

```css
.button {
  transition-property: background-color, transform, box-shadow;
  transition-duration: 160ms;
  transition-timing-function: ease;
  transition-delay: 0ms;
}
```

What each part means:

- `transition-property` says which visual properties should animate.
- `transition-duration` says how long the change takes.
- `transition-timing-function` says how the motion speeds up or slows down.
- `transition-delay` says how long to wait before the transition starts.

Design intent:

- soften a state change
- make the interface feel responsive
- avoid distracting motion

Prefer naming the properties you animate:

```css
transition: background-color 160ms ease, transform 160ms ease;
```

Be careful with:

```css
transition: all 0.3s ease;
```

It is easy to write, but it can animate properties you did not intend to animate.

## Keyframe animations

Keyframes describe an animation with multiple moments.

Use keyframes when something needs to move by itself, not only between interaction states.

```css
@keyframes pulse {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.04);
  }

  100% {
    transform: scale(1);
  }
}

.status-dot {
  animation: pulse 1200ms ease-in-out infinite;
}
```

The same idea can be written in a longer form:
```css
.status-dot {
  animation-name: pulse;
  animation-duration: 1200ms;
  animation-timing-function: ease-in-out;
  animation-delay: 0ms;
  animation-iteration-count: infinite;
  animation-direction: normal;
  animation-fill-mode: none;
  animation-play-state: running;
}
```

What each part means:

- `animation-name` says which `@keyframes` animation to use.
- `animation-duration` says how long one full animation cycle takes.
- `animation-timing-function` says how the motion speeds up or slows down.
- `animation-delay` says how long to wait before the animation starts.
- `animation-iteration-count` says how many times the animation should run.
- `animation-direction` says whether the animation runs forward, backward, or alternates.
- `animation-fill-mode` says whether the element keeps styles from the animation before or after it runs.
- `animation-play-state` says whether the animation is running or paused.

Good uses:

- loading indicators
- attention on a new item
- success confirmation
- skeleton loading
- subtle status indicators

Avoid:

- infinite animations on large areas
- motion that competes with reading
- animations that are too slow for frequent actions
- using animation to hide unclear interaction design

## How to brief an AI agent

A good prompt describes the states and the design intent, not only the CSS property.

Weak prompt:

> Add hover animation.

Better prompt:

> Add interaction states to the primary button. On hover, make it feel clickable with a slightly darker background, a small lift, and a softer shadow. On active, make it compress quickly. Add a visible keyboard focus ring using `:focus-visible`. Keep transitions under 200ms and do not shift nearby layout.

Another useful prompt:

> Review the interaction states in this component. Check hover, active, and keyboard focus. Tell me if the motion is too strong, if focus is missing, or if any state causes layout shift.

## Quality checklist

Use this checklist when reviewing AI-generated interaction work.

- The element clearly looks interactive before hover.
- Hover makes the action clearer, not confusing.
- Active gives quick feedback when pressing.
- Keyboard focus is visible and high contrast.
- The interaction works with keyboard navigation.
- Motion is short and purposeful.
- The layout does not jump when states change.
- Text remains readable in every state.
- Hover is not the only way to access important information.
- Repeated or infinite animation does not distract from the task.

## Examples

Live examples:

- [Interaction states demo](./examples/states-demo.html)
- [Motion demo](./examples/motion-demo.html)

## Exercise

Improve a product/blog listing page with interaction states and motion.

Starter files:

- [Exercise HTML](./exercise/index.html)
- [Exercise CSS](./exercise/styles.css)

The page already has working layout, cards, text, links, and buttons. The task is to make the interface feel more interactive without changing the HTML structure too much.

Requirements:

- Add hover, active, and focus-visible states to the main buttons.
- Add hover and focus-visible states to the navigation links.
- Add a hover state to each listing card.
- Add one subtle keyframe animation to the "Featured" badge.
- Add transitions only to the properties that should animate.
- Keep all transitions short and intentional.
- Check the result with mouse and keyboard.
- Avoid layout shift when hovering or focusing.

Prompt you can give to an AI agent:

> Improve the interaction states on this listing page. Add polished hover, active, and focus-visible states to buttons, navigation links, and cards. Add one restrained keyframe animation to the Featured badge. Keep transitions under 220ms, animate only intentional properties, avoid layout shift, and keep keyboard focus clearly visible.

Review questions:

- Which elements are interactive before hover?
- What changes on hover?
- What changes while pressing?
- Is keyboard focus visible?
- Does any animation distract from reading?
- Did any state cause the layout to jump?

## Resources

- [Pseudo-classes on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
- [:hover on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)
- [:active on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:active)
- [:focus-visible on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible)
- [Using CSS transitions on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_transitions/Using_CSS_transitions)
- [Using CSS animations on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animations/Using_CSS_animations)
- [DEV course website](https://dev-course-phi.vercel.app/)
