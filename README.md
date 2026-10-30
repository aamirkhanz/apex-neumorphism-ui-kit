# Neumorphism UI Kit for Oracle APEX

A soft, tactile look for Oracle APEX Universal Theme: surfaces share the page color and are raised or pressed in. One CSS file styles every Universal Theme component, in light and dark mode, without changing your pages, templates or template options.

[![Live demo](https://img.shields.io/badge/Live_demo-5468ee?style=for-the-badge)](https://oracleapex.com/ords/r/aamirkhanz/plugins/neumorphism-ui-kit) &nbsp; Sign in as `demo` with the password `Demo`.

![Overview in light mode](screenshots/overview-light.png)

| | |
|---|---|
| **Files** | `neumorphism.css` (the look), `neumorphism.js` (optional light/dark switch) |
| **Version** | 1.0.5 |
| **Built for** | Oracle APEX 26.2, Universal Theme with the Iris theme style (tested); other styles are not tested yet |
| **License** | MIT |

## What it styles

Every component of the Universal Theme reference: Alert, Avatar, Badge, Badges List, Breadcrumb, Button, Button Container, Button Group, Calendar, Card Regions, Card Templates, Carousel, Charts, Classic Report, Collapsible, Column Toggle Report, Comments, Content Block, Content Row, Contextual Info, Flexbox Container, Form Field (every item type and label template), Help Text, Hero, Image, Inline Dialog, Interactive Grid, Interactive Report, Links List, List View, Media List, Menu Bar, Menu Popup, Metric Card, Navigation Bar, PL/SQL Dynamic Content, Reflow Report, Region Display Selector, Standard, Static Content, Tabs Container, Timeline, Title Bar and Tree.

It also styles the page shell (header, side navigation, title bar, footer), modal and inline dialogs, drawers, popups, menus, page messages, tooltips, the date picker, Faceted Search, the rich text editor and select lists.

## Install

1. Download `neumorphism.css` and, for the light/dark switch, `neumorphism.js` from the [latest release](https://github.com/aamirkhanz/apex-neumorphism-ui-kit/releases/latest) or from this repository.
2. In App Builder, go to **Shared Components > Static Application Files** and upload both files.
3. Go to **Shared Components > User Interface Attributes** and add:
   - CSS File URLs: `#APP_FILES#neumorphism.css`
   - JavaScript File URLs: `#APP_FILES#neumorphism.js`

That's all: every page of the application now uses the kit. Remove the two URLs to go back to plain Universal Theme.

## Dark mode

![Forms in dark mode](screenshots/forms-dark.png)

`neumorphism.js` switches between light and dark and remembers the choice (localStorage `nm-mode`); until the user chooses, it follows the operating system.

- Add a button or link with the attribute `data-nm-mode-toggle`, or call `neumorphism.toggle()`.
- `neumorphism.setMode( "light" | "dark" | "auto" )` sets a mode; `neumorphism.getMode()` returns the current one.
- `<html>` fires `nm-modechange` with `detail.mode` after a change, for example to redraw charts.

To open each page in the saved mode without a flash, put this snippet in the page template's HTML header, before the CSS:

```html
<script>(function(d){var m;try{m=localStorage.getItem("nm-mode")}catch(e){}
if(m!=="dark"&&m!=="light")m=matchMedia("(prefers-color-scheme: dark)").matches?"dark":"light";
d.documentElement.classList.add("nm-"+m)})(document);</script>
```

Without the JavaScript, the kit is light; add the class `nm-dark` to `<html>` yourself for dark.

## Make it yours

Override the tokens in your own CSS, loaded after the kit:

```css
:root { --nm-accent: #0e9f6e; --nm-accent-2: #0b7a55; --nm-radius: 14px; --nm-depth: 4px; }
html.nm-dark { --nm-accent: #34d399; }
```

| Token | What it sets |
|---|---|
| `--nm-bg` | Page and surface color |
| `--nm-well` | Background of pressed-in fields |
| `--nm-accent`, `--nm-accent-2` | Accent color and the end of its gradient (hot buttons, brand, selections) |
| `--nm-text`, `--nm-text-2` | Text and secondary text |
| `--nm-shadow-light`, `--nm-shadow-dark` | The highlight and the shadow that make the depth |
| `--nm-depth` | How far surfaces stand out (default 5px) |
| `--nm-radius`, `--nm-radius-sm` | Corner rounding of regions, and of buttons and fields |
| `--nm-success`, `--nm-warning`, `--nm-danger`, `--nm-info` | Status colors |

For your own regions, items and HTML, add a CSS class: `nm-raised`, `nm-raised-sm`, `nm-inset`, `nm-flat`, `nm-convex`, `nm-pill` or `nm-accent`.

## Screenshots

| | |
|---|---|
| ![Buttons](screenshots/buttons-light.png) | ![Alerts](screenshots/alerts-light.png) |
| ![Cards in dark mode](screenshots/cards-dark.png) | ![Interactive Report](screenshots/reports-light.png) |
| ![Overview in dark mode](screenshots/overview-dark.png) | ![Charts in dark mode](screenshots/charts-dark.png) |

## Notes

- **No markup changes.** The kit only overrides Universal Theme's CSS variables and adds depth to its components; your templates and template options stay standard.
- **Accessibility.** Text keeps WCAG AA contrast on the surfaces, fields have a darker well so they read as fields, keyboard focus always shows a ring, and motion is reduced when the user asks for it.
- **Select lists.** In browsers with customizable selects (Chrome and Edge 135 and later) the open list takes the kit's style; other browsers show their native list.
- **Charts.** Chart series keep the colors you set in each chart; the kit styles the region around them.

## License

MIT, see [LICENSE](LICENSE).

## More

Plug-ins and updates for Oracle APEX by [TechRevX](https://www.techrevx.com).
