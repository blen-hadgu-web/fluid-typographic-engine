# The Fluid Typographic Engine

A responsive magazine editorial demonstrating system-wide design tokens, mathematically balanced fluid typography, an optimal reading measure, vertical rhythm, and progressive optical text trimming.

## Live Website

After GitHub Pages is enabled:

`https://blen-hadgu-web.github.io/fluid-typographic-engine/`

## Public Repository

`https://github.com/blen-hadgu-web/fluid-typographic-engine`

## Project Structure

```text
fluid-typographic-engine/
├── .nojekyll
├── favicon.svg
├── index.html
├── README.md
├── SUBMISSION.txt
├── TESTING-CHECKLIST.md
├── VIDEO-SCRIPT.md
└── styles.css
```

## Run Locally

No package manager, framework, JavaScript, or build process is required.

1. Download or clone the repository.
2. Open `index.html` in a modern browser.

VS Code Live Server may also be used.

## AI Tool and Prompt

**AI tool:** ChatGPT

### Drafting prompt

> Act as a senior design technologist and generate a CSS stylesheet for the supplied semantic magazine-article HTML.
>
> Create a system-wide responsive type scale using CSS custom properties declared in `:root`, using token names such as `--size-step--1`, `--size-step-0`, `--size-step-1`, and larger steps. Do not place hardcoded font-size values directly on article elements; every element must reference a type token.
>
> The `h1`, `h2`, and `blockquote` sizes must use `clamp()`. Each preferred value must combine `rem` and `vw` so browser zoom can enlarge the text. Provide a clear minimum, fluid middle expression, and maximum.
>
> Constrain the article body to between 65 and 75 characters per line using `ch`. Create a unified vertical rhythm with inherited custom properties for type, line-height, and spacing.
>
> Apply `text-box: trim-both cap alphabetic` to `.article-category`, `.article-title`, and `.drop-cap`. Treat it as progressive enhancement: provide baseline-grid fallbacks using unitless line-height, relative margins, and padding, then apply `text-box` inside `@supports`.
>
> Do not set `html { font-size: 62.5%; }`. Respect the user's browser root font size. Avoid large breakpoint-based type changes; the typography must scale continuously.
>
> Use low-specificity selectors, cascade layers, relative units, semantic-friendly styling, visible keyboard focus, reduced-motion support, and accessible light/dark colors.

## System-Wide Type Tokens

```css
--size-step--1: clamp(0.875rem, 0.831rem + 0.188vw, 1rem);
--size-step-0: clamp(1rem, 0.956rem + 0.188vw, 1.125rem);
--size-step-1: clamp(1.25rem, 1.162rem + 0.376vw, 1.5rem);
--size-step-2: clamp(1.5rem, 0.972rem + 2.254vw, 3rem);
--size-step-3: clamp(1.25rem, 0.81rem + 1.878vw, 2.5rem);
--size-step-4: clamp(2.25rem, 1.458rem + 3.38vw, 4.5rem);
--size-step-5: clamp(3.5rem, 2.62rem + 3.756vw, 6rem);
```

The scale was calculated across a viewport range of 375 to 1440 CSS pixels. Each preferred expression mixes a root-relative intercept with a viewport-width slope.

## Fluid Math Example

The title scales from 2.25rem to 4.5rem.

At a 16-pixel browser default, that is 36px to 72px.

```text
slope = (72 - 36) / (1440 - 375)
      = 36 / 1065
      ≈ 0.03380

vw coefficient = 0.03380 × 100
               ≈ 3.38vw

intercept = 36 - (0.03380 × 375)
          ≈ 23.32px
          ≈ 1.458rem
```

Final token:

```css
--size-step-4: clamp(2.25rem, 1.458rem + 3.38vw, 4.5rem);
```

The maximum is twice the minimum, and the preferred expression contains `rem`, helping the title remain responsive to browser zoom.

## Reading Measure

The article body is limited to:

```css
--measure: 70ch;
```

```css
.article-body {
  max-inline-size: var(--measure);
}
```

This stays within the assignment's required range of 65 to 75 characters.

## Vertical Rhythm

The type scale, unitless line-height tokens, and relative spacing tokens are declared in `:root` and inherited throughout the article. Flow spacing is applied using:

```css
.article-body > * + * {
  margin-block-start: var(--flow-space, var(--space-md));
}
```

Headings and blockquotes override only `--flow-space`, preserving the system instead of adding one-off margins.

## Optical Text Trimming

The category, title, and drop cap have readable fallback line heights, relative padding, and baseline offsets.

Supporting browsers receive:

```css
@supports (text-box: trim-both cap alphabetic) {
  .article-category,
  .article-title,
  .drop-cap {
    text-box: trim-both cap alphabetic;
  }
}
```

The project intentionally does not use an invented or unreliable vendor-prefixed property. Unsupported browsers retain the baseline-grid fallback.

## Human Audit

### Fluid scaling integrity

- The stylesheet does not use breakpoint-based font-size changes.
- Every major type size uses a bounded `clamp()`.
- Resize the browser slowly and watch the computed font size change continuously.

### Zoom accessibility

- No pure-viewport font-size values are used.
- The preferred expressions combine `rem` and `vw`.
- The page is tested at 200% zoom for text growth, reflow, and overlap.

### Reading length

- The body measure is exactly `70ch`.
- It remains centered and narrow on wide displays.

### Cascade isolation

- The browser's root font size is not changed.
- There is no `html { font-size: 62.5%; }`.
- Type tokens are based on `rem` and flow through inheritance.
- There is no `!important`.

## Current Feature Note

`text-box` is a progressive CSS feature. The page does not depend on it for readability or layout. The fallback remains active in browsers that do not support the shorthand.

## Deployment

1. Create a public repository named `fluid-typographic-engine`.
2. Push or upload the project files.
3. Open **Settings → Pages**.
4. Select **Deploy from a branch**.
5. Choose `main` and `/(root)`.
6. Save and wait for the deployment.

## Testing

See [`TESTING-CHECKLIST.md`](TESTING-CHECKLIST.md).

The separate “Web Project Testing & Quality Assurance Guide” was not included with the assignment text supplied for this project. The checklist covers all visible requirements and common accessibility, responsive, semantic, and production tests.

## Author

**Blen Hadgu**
