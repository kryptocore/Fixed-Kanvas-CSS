# Fixed Kanvas CSS Boilerplate v1.7

I designed this for my more esoteric web projects that require a fixed, non-scrolling viewport. Ideal for artistic, experimental, or unconventional web designs.

Disclaimer: This boilerplate is **non-standard** and really isn't suitable for typical web projects that require scrolling or responsive content flow. It was created to meet my specific artistic needs and may require additional consideration when used in other contexts.

## What it do tho:

- Fixed Viewport: Forces the webpage to fit within the viewport dimensions, preventing scrolling.
- CSS Nesting: Utilizes the new CSS nesting syntax specifications to keep things tidy and collapsible.
  - [CSS nesting is supported in all major browsers](https://caniuse.com/?search=nesting)... except for the 5 people currently using Firefox ESR (as of 30OCT24). 😠
- Feature Queries: Uses `@supports` to provide `vh` fallback for browsers that do not yet support `svh`.
- Modern Units: Incorporates the new-ish `svh` (Small Viewport Height) unit for more accurate sizing on mobile devices.
- Zero Edges: Resets `margin` and `padding` for all elements to ensure a consistent layout.

---
### Commented Preview:

```css
html {
    /* CSS variable for height, initally 100vh (100% of the height of the viewport). */
    --full-height: 100vh;  

    /* If supported, change height to use `svh`. This fixes unintentional overflow on mobile. */
    @supports (height: 100svh) {
        --full-height: 100svh;
    }                               

    box-sizing: border-box;
    height: var(--full-height);
    overflow: hidden;
    /* Normalize text inflation algorithm on mobile. */
    -webkit-text-size-adjust: 100%;
    text-size-adjust: 100%;

    /* Zero all edges for all elements in <html> */
    & *,
    *::before,
    *::after {
        margin: 0;
        padding: 0;
        box-sizing: inherit;
    }                               

    & body { 
        /* Fix <body> to viewport. */
        position: fixed;            
        z-index: 0;
        width: 100vw;
        height: var(--full-height);
        overflow: hidden;
    }
}
```

Mind the license and don't forget to include `<meta name="viewport" content="width=device-width, initial-scale=1.0">` in your `<head>` ! ❤️
