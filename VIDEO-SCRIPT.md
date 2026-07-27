# Video Demonstration Script

Suggested duration: 3–5 minutes.

## 1. Introduction

“Hi, my name is Blen Hadgu. This is my Fluid Typographic Engine magazine article. I used AI to draft the design system, then audited and corrected the typography, cascade, reading measure, optical trimming, and accessibility.”

## 2. Functionality walkthrough

Open the live website and show:

1. The category badge
2. Main title
3. Lead paragraph
4. Published date
5. Drop cap
6. Subheadings
7. Blockquote
8. Article footer

Resize the browser slowly from narrow to wide.

Say:

“The typography changes continuously rather than snapping at type breakpoints.”

## 3. Type-token audit

Open `styles.css` and show the custom properties in `:root`.

Show:

```css
--size-step-0
--size-step-2
--size-step-3
--size-step-4
--measure
```

Say:

“All article font sizes reference system tokens. The body respects the browser root size because the HTML element is not reset to 62.5 percent.”

## 4. Fluid calculation

Show:

```css
--size-step-4: clamp(2.25rem, 1.458rem + 3.38vw, 4.5rem);
```

Explain:

“The first value is the minimum, the middle mixes rem and viewport width, and the final value is the maximum.”

Open DevTools, inspect the title, and slowly resize the browser while showing the computed font size.

## 5. Zoom test

Zoom to 200%.

Show that:

- The type grows
- The title reflows
- The body remains readable
- No text overlaps
- There is no horizontal page scrolling

## 6. Reading-measure test

Show:

```css
--measure: 70ch;
```

Then show the article on a wide viewport.

Say:

“The article body is limited to 70 characters, inside the required 65-to-75-character range.”

## 7. Cascade-isolation test

Search the stylesheet for:

```text
62.5%
!important
```

Show that both searches return zero results.

Display the cascade-layer declaration:

```css
@layer reset, tokens, base, layout, components, utilities;
```

## 8. Optical trimming test

Inspect the category, title, or drop cap.

Show the fallback styles, then locate:

```css
text-box: trim-both cap alphabetic;
```

Disable and re-enable it if supported.

Say:

“Text-box is progressive enhancement. Unsupported browsers keep the baseline-grid fallback, so readability does not depend on this feature.”

## 9. Testing checklist

Open `TESTING-CHECKLIST.md` and briefly show completed cases for:

- Semantics
- Fluid scaling
- 200% zoom
- 70ch measure
- Cascade isolation
- Text trimming
- Responsive layouts
- Live deployment

## 10. Deployment proof

Show:

```text
Repository:
https://github.com/blen-hadgu-web/fluid-typographic-engine

Live page:
https://blen-hadgu-web.github.io/fluid-typographic-engine/
```

Open the live link in an Incognito/Private window.

## 11. Closing

“The project uses a unified, zoom-friendly typographic system instead of breakpoint-heavy CSS. Thank you.”
