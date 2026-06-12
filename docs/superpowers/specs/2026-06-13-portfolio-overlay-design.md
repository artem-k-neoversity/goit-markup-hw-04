# Portfolio Overlay Design

## Goal

Implement requirements `C9-C11` for the `Our Portfolio` cards:

- show the text overlay when hovering anywhere on the card;
- animate the blue overlay from the bottom upward;
- keep pseudo-elements decorative only, without text content.

## Scope

Changes are limited to:

- `index.html` for card markup in the `Our Portfolio` section;
- `css/styles.css` for overlay layout, animation, and hover behavior.

## Markup Changes

Each portfolio card gets:

- an image wrapper element that becomes the clipping area for the overlay;
- a dedicated overlay element containing the same text in all six cards;
- the existing `.content` block remains below the image area unchanged.

Recommended structure per card:

```html
<li>
  <div class="image-box">
    <img ... />
    <p class="overlay">...</p>
  </div>
  <div class="content">...</div>
</li>
```

## Styling Changes

The image wrapper:

- uses `position: relative`;
- uses `overflow: hidden` so the overlay stays inside image bounds.

The overlay:

- is absolutely positioned over the image;
- fills the full image area;
- uses the blue project color background;
- starts below the visible area with `transform: translateY(100%)`;
- transitions with `transform 250ms cubic-bezier(0.4, 0, 0.2, 1)`.

The card hover state:

- keeps the existing shadow transition on the whole card;
- reveals the overlay from the bottom on `li:hover` and `li:focus`.

## Interaction Rules

- Hovering anywhere on a portfolio card triggers the overlay animation.
- The overlay slides upward from bottom to top.
- No pseudo-element contains text; existing navigation `::after` remains decorative with `content: ""`.

## Shared Overlay Text

All six cards use the same overlay text:

`14 Stylish and User-Friendly App Design Concepts · Task Manager App · Calorie Tracker App · Exotic Fruit Ecommerce App · Cloud Storage App`

## Validation

Success criteria:

- `C9`: overlay appears from card hover, not only from image hover;
- `C10`: overlay enters from below using vertical transform animation;
- `C11`: pseudo-elements do not carry textual content.
