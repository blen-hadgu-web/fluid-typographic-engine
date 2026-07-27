# Web Project Testing and Quality Assurance Checklist

Use this checklist during the required video. Add any additional tests from the instructor's separate QA guide if one is provided.

## 1. Content and semantics

- [ ] The page title is “The Architecture of Fluid Layouts.”
- [ ] The article uses an `article` element.
- [ ] The article has a semantic `header` and `footer`.
- [ ] The publication date uses a valid `time` element.
- [ ] Heading order is sequential: one `h1`, followed by `h2` headings.
- [ ] The quotation uses `blockquote`.
- [ ] The drop cap is hidden from assistive technology and the complete word remains available to screen readers.
- [ ] The skip link appears when focused.

## 2. Type-token system

- [ ] All font sizes originate from custom properties in `:root`.
- [ ] Search `styles.css` for `font-size:` and verify article selectors use `var(...)`.
- [ ] The scale includes body, lead, heading, quote, title, and drop-cap steps.
- [ ] Unitless line-height tokens control the vertical rhythm.
- [ ] Spacing values come from the root spacing scale.

## 3. Fluid scaling integrity

- [ ] `h1` references a `clamp()` token.
- [ ] `h2` references a `clamp()` token.
- [ ] `blockquote` references a `clamp()` token.
- [ ] Each clamp has a minimum, preferred value, and maximum.
- [ ] Each preferred value mixes `rem` and `vw`.
- [ ] Slowly resize the browser and verify that type changes continuously.
- [ ] Confirm there are no media-query font-size jumps.

## 4. Browser zoom

- [ ] Test the page at 100%.
- [ ] Test the page at 200%.
- [ ] Typography is visibly larger at 200%.
- [ ] Text reflows without overlap.
- [ ] No content is clipped.
- [ ] No page-level horizontal scrolling occurs.
- [ ] Navigation by keyboard remains possible.

## 5. Reading measure

- [ ] `.article-body` uses `max-inline-size: var(--measure)`.
- [ ] `--measure` equals `70ch`.
- [ ] The measure falls within the required 65–75 character range.
- [ ] Body lines remain comfortably narrow on a wide monitor.
- [ ] Body content remains readable on a narrow phone.

## 6. Cascade isolation

- [ ] The stylesheet uses cascade layers.
- [ ] `:root` contains the type, spacing, color, and measure tokens.
- [ ] `html` does not set a reduced percentage font size.
- [ ] Search for `62.5%` and confirm there are no results.
- [ ] Search for `!important` and confirm there are no results.
- [ ] Selectors remain low-specificity.
- [ ] User root font-size preferences remain effective.

## 7. Optical trimming

- [ ] `.article-category` has a line-height and padding fallback.
- [ ] `.article-title` has a tight line-height fallback.
- [ ] `.drop-cap` has a relative baseline offset and line-height fallback.
- [ ] `text-box: trim-both cap alphabetic` is inside `@supports`.
- [ ] Inspect the category, title, or drop cap in DevTools.
- [ ] Disable `text-box` and observe the fallback.
- [ ] Re-enable `text-box` and compare the optical alignment.
- [ ] In an unsupported browser, confirm the layout remains readable.

## 8. Responsive and visual testing

Test at narrow phone, large phone, tablet, laptop, and wide desktop sizes.

- [ ] Page padding scales fluidly.
- [ ] The title wraps naturally.
- [ ] The lead remains narrower than the page.
- [ ] The article body remains centered.
- [ ] The blockquote does not overflow.
- [ ] The drop cap does not obscure the first paragraph.
- [ ] Light mode has readable contrast.
- [ ] Dark mode has readable contrast.

## 9. Accessibility and preferences

- [ ] Focus indicators are visible.
- [ ] The page works with keyboard navigation.
- [ ] The page remains readable with reduced motion enabled.
- [ ] The document language is English.
- [ ] Logical properties are used for writing-direction-friendly spacing.

## 10. Production deployment

- [ ] The GitHub repository is public.
- [ ] `index.html` is at the repository root.
- [ ] `styles.css` loads from the live page.
- [ ] The favicon loads.
- [ ] GitHub Pages reports a successful deployment.
- [ ] The live link works in an Incognito/Private window.
- [ ] The README documents the project, prompt, audit, and local setup.
