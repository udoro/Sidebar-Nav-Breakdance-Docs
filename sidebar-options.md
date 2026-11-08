---
icon: sliders
---

# Sidebar Options

The options are in the **JavaScript** field of the **Sidebar Nav Codes** Code Block, at the top, inside `DWCSidebarConfig`. Set an option to `1` to turn it on and `0` to turn it off.

```js
const DWCSidebarConfig = {
    enableOffCanvas: 0,
    enableCollapsibleSidebar: 1,
    // ...
};
```

Change the number only. Don't touch the code below `urlConfigMap`: that is the sidebar's own code.

The **Template value** column is what the option is set to when you paste the template.

***

## Navigation

| Option | Template value | What it does |
| --- | --- | --- |
| `updateBackText` | `1` | The Back button reads "back to" and the name of the panel it goes back to, for example "back to Home". |
| `autoCurrentPosition` | `1` | When a page loads, the sidebar slides to the panel that holds the link to that page. If the link is in a dropdown, the dropdown opens whatever this option is set to. |
| `enableTopBar` | `0` | Adds a bar across the top of the page, above the sidebar. The **header inner wrap**, with the logo and buttons, becomes the bar. Needs `enableOffCanvas` set to `0`. Also set the `topbar` attribute to `1`. |

## Off-canvas

| Option | Template value | What it does |
| --- | --- | --- |
| `enableOffCanvas` | `0` | Hides the sidebar off the screen. A menu button in a top bar opens it over the page. This also turns off the collapsible sidebar. Also set the `offcanvas` attribute to `1`. |
| `offCanvasPushContent` | `0` | When the off-canvas sidebar opens, it pushes the page aside instead of covering it. Needs `enableOffCanvas` set to `1`. This turns off headroom. |
| `fixedNavTrigger` | `1` | With push content, keeps the menu button in place, so it doesn't slide off the screen. Desktop only. |
| `mobileMenuAboveHeader` | `0` | The mobile and off-canvas menu opens over the top bar instead of below it. |

{% hint style="warning" %}
When you turn on `enableOffCanvas` or `enableTopBar`, also change the matching attribute on the **Sidebar &lt;header&gt;** section: `offcanvas` or `topbar`. Set it to `1`. If an attribute is `1` and its option is `0`, the layout breaks. See [Attributes & Classes](attributes-and-classes.md#sidebar-attributes).
{% endhint %}

## Dropdowns

| Option | Template value | What it does |
| --- | --- | --- |
| `openFirstDropDown` | `0` | Opens the first dropdown when the page loads. |
| `autoCloseDropdown` | `1` | Closes a dropdown when keyboard focus leaves it. |

## Overlay

| Option | Template value | What it does |
| --- | --- | --- |
| `overlaySidebar` | `0` | The sidebar sits over the page content instead of beside it. Use it on full-width pages. Needs `enableOffCanvas` set to `0`. |
| `overlayTopBar` | `0` | The top bar sits over the page content instead of taking up space. Needs `enableOffCanvas` set to `1`. |

## Headroom and scrolling

| Option | Template value | What it does |
| --- | --- | --- |
| `enableHeadroom` | `1` | The top bar hides when you scroll down and comes back when you scroll up. It only works when `enableOffCanvas` or `enableTopBar` is `1`, and not with `offCanvasPushContent`. |
| `offsetHashLinkScroll` | `0` | When a link jumps to a section on the same page, the section stops below the top bar instead of under it. |
| `calcTopPadding` | not in the template | Adds top padding to the first section of the page, so the top bar doesn't cover it. With the top bar, the template already does this. With off-canvas on desktop, add the line `calcTopPadding: 1,` to `DWCSidebarConfig` to turn it on. |

## Right to left

| Option | Template value | What it does |
| --- | --- | --- |
| `enableRTL` | `0` | Sets the whole page to right to left. The sidebar moves to the right side, and text direction changes too. You don't need it if your site is already in a right-to-left language. |

## Collapsible sidebar

The collapsible sidebar works on desktop only. It doesn't work when `enableOffCanvas` is `1`, at any screen width.

| Option | Template value | What it does |
| --- | --- | --- |
| `enableCollapsibleSidebar` | `1` | Turns on the **Collapse toggle** button. It shrinks the sidebar to its icons. |
| `collapseOnPageLoad` | `0` | The sidebar starts collapsed. |
| `restoreActivePanelOnExpand` | `1` | When the sidebar expands again, it goes back to the panel and dropdowns that were open. |
| `saveCollapseState` | `1` | Remembers whether the visitor collapsed the sidebar, across pages and reloads. It's saved in the visitor's browser. |
| `hoverToExpandSidebar` | `0` | While collapsed, the sidebar expands when the mouse is over it and collapses when the mouse leaves. |
| `collapseAutoWidth` | `1` | Works out the collapsed width from the icon size and the padding variables. Set it to `0` to use the `--sidebar-collapse-width` variable instead. See [Collapsed width](styling.md#collapsed-width). |

To make the collapsible sidebar cover the page instead of pushing it, see the `data-overlap-collapsible` attribute in [Attributes & Classes](attributes-and-classes.md#sidebar-attributes).

## Tooltips

| Option | Template value | What it does |
| --- | --- | --- |
| `enableTooltips` | `1` | When the sidebar is collapsed, each link, button and dropdown shows its text in a tooltip on hover. |
| `debugTooltips` | `0` | Writes a line to the browser console for each tooltip it sets up. Use it only while you fix a tooltip problem. |

## Page transitions

| Option | Template value | What it does |
| --- | --- | --- |
| `reinitOnUrlChange` | `true` | Restarts the sidebar when the page address changes without a full page load, for example with AJAX page transitions. Set it to `false` to turn it off. See [Page Transitions & JavaScript](guides/javascript-api.md). |

## Breakpoints

| Option | Template value | What it does |
| --- | --- | --- |
| `mq` | `window.matchMedia("(max-width: 1024px)")` | The mobile breakpoint. At this width and below, the sidebar becomes a mobile menu. To change it, see [Change the breakpoint](#change-the-breakpoint). |
| `offCanvasBreakpoint` | `window.matchMedia("(max-width:10024px)")` | With `enableOffCanvas` on, off-canvas works at this width and below. The template value covers every screen. |

{% hint style="info" %}
The template also lists `calcHeaderHeight`. It doesn't change anything in 3.0.3. Leave it as it is.
{% endhint %}

***

## Change the breakpoint

The breakpoint is where the sidebar becomes the mobile menu. By default, the mobile menu shows at 1024px and below, and the sidebar from 1025px.

Change it in four places, all inside the **Sidebar Nav Codes** Code Block. If you only change the JavaScript option, the layout breaks between the old width and the new one.

1. **JavaScript** field: in `mq`, change `1024px` to your new mobile width, for example `991px`.
2. **CSS** field: find `@media (min-width: 1025px)` and change `1025px` to your new desktop width, for example `992px`.
3. **CSS** field: find `@media(max-width:1024px)` and change `1024px` to your new mobile width, `991px`.
4. **CSS** field: find `@media (max-width:1024px)` and change `1024px` to `991px` too.

The desktop width is always 1px more than the mobile width.

This is the one change you make outside the options and the variables at the top.

***

## Common setups

Set these options. Leave the others at their template values.

| You want | Set |
| --- | --- |
| A sidebar that collapses to icons | Nothing. It is on in the template. |
| The same, opening on hover | `hoverToExpandSidebar: 1` |
| A sidebar that starts collapsed | `collapseOnPageLoad: 1` |
| A menu button that opens the sidebar, on every screen | `enableOffCanvas: 1`, and the `offcanvas` attribute to `1` |
| The same, pushing the page aside | `enableOffCanvas: 1`, `offCanvasPushContent: 1`, and the `offcanvas` attribute to `1` |
| A bar across the top, with the sidebar below it | `enableTopBar: 1`, and the `topbar` attribute to `1` |
| The sidebar on the right | `enableRTL: 1` |

Below the breakpoint, the sidebar is always a mobile menu that opens from the menu button. You don't need off-canvas for that.

***

## Different settings on different pages

Below `DWCSidebarConfig`, in the same JavaScript field, `urlConfigMap` changes options on chosen pages. Add one line per page:

```js
const urlConfigMap = {
  '/docs': { enableOffCanvas: 1, enableCollapsibleSidebar: 0 },
  '/blog': { enableCollapsibleSidebar: 1, collapseOnPageLoad: 1 }
};
```

On `/docs` the sidebar is off-canvas and doesn't collapse. On `/blog` it collapses and starts collapsed. Every other page uses `DWCSidebarConfig`.

* **The key is the page's path.** Start it with `/`, and leave out your domain and the last `/`. For `https://example.com/docs/`, write `'/docs'`. For your home page, write `''`.
* **Only that exact page matches.** `'/docs'` doesn't cover `/docs/intro`. Add a line for each page.
* **List only the options you want to change.** The page keeps the other options from `DWCSidebarConfig`.
* **The template's examples do nothing.** They sit inside a comment, between `/*` and `*/`. Add your lines outside the comment.
* **Attributes don't change per page.** The `offcanvas` and `topbar` attributes are on the header, so they are the same on every page. A page that turns on off-canvas in `urlConfigMap` works, but its first frame can flash before the sidebar settles.
