---
icon: sparkles
---

# AI Skills Reference Tables

Sidebar Navigation Builder for Breakdance, version 3.0.3. Grep the section you need. Never read this file in full.

Customer docs: https://design-with-cracka.gitbook.io/sidebarnavbreakdance

## 1. Fingerprint

* Root element: `Section`, tag `header`, id `dwc_header`, classes `dwc-sidebar` and `dwc-offcanvas-header`. Label `Sidebar  <header> v3.0.2` (the label is older than the code).
* The Code Block: label `Sidebar Nav Codes`, the last child of the root. Its `javascript_code` starts with `const DWCSidebarConfig = {` and holds the options, `urlConfigMap` and the engine (`class DWCSidebarNavigation`). Its `css_code` starts with the `:root` variables. About 84 KB of JS and 53 KB of CSS. Its last JS line logs `<Sidebar Nav Builder v3.0.2>`.
* Element types stored in the template: `Section`, `Div`, `WrapperLink`, `Text`, `Icon`, `Heading`, `HtmlImg`, `Button`, `CodeBlock`. Most of these are not in `breakdance-get-element-slugs`.
* On the published page the JS runs inside a `DOMContentLoaded` function inside a `<script>`. The CSS comes from a generated stylesheet.

For another version, compare the live option names and attributes with sections 3 and 4. The live code wins.

## 2. Element map

Labels are the template's. Users can rename them: match by class first.

| Label | Type | Tag | Classes | Attributes | Notes |
| --- | --- | --- | --- | --- | --- |
| Sidebar  <header> v3.0.2 | Section | `header` | `dwc-sidebar`, `dwc-offcanvas-header` | section 4 | Root. id `dwc_header`. |
| header inner wrap | Div | | `dwc-header-inner-wrap` | | Top of the sidebar; the top bar with `enableTopBar` or `enableOffCanvas`. Children: Logo wrapper, trigger wrapper, Collapse toggle. |
| Logo wrapper | Div | | `dwc-sidebar__logo-wrapper` | | Child: WrapperLink (`aria-label` is the site title) > HtmlImg. |
| trigger wrapper | Div | | `push-fixed` | | Child: mobile menu trigger. |
| mobile menu trigger | Div | | `dwc-nav-trigger` | `tabindex` `0`, `role` `button`, `aria-label` | Opens the mobile and off-canvas menu. |
| Collapse toggle | Div | | `dwc-toggle-collapse` | `role` `button`, `data-static` | Child: Icon. |
| Nav | Div | `nav` | `dwc-sidebar__nav` | | Every panel is a direct child. |
| close btn | Div | | `dwc-sidebar__nav-close-btn` | `tabindex`, `role`, `aria-label` | Closes the mobile and off-canvas menu. |
| Home panel | Div | | `dwc-sidebar__nav__panel`, `dwc-sidebar__nav__panel--home` | `data-title` `Home` | Children: inner wrap, panel footer. |
| Slide Panel | Div | | `dwc-sidebar__nav__panel`, `dwc-slide-right` | `data-title` | Children: Panel header, inner wrap. Keep `dwc-slide-right` on every non-home panel. |
| inner wrap | Div | | `dwc-nav__panel__inner` | | |
| Panel header | Div | | `dwc-nav__panel__header` | | Children: Home button, Back button. |
| Home button | Div | | `dwc-nav__home-btn` | `role`, `tabindex`, `title` | Children: icon, Text `nav__home-btn__txt`. |
| Back button | Div | | `dwc-sidebar__nav__btn`, `dwc-nav__back-btn` | `role`, `tabindex` | Children: chevron-left Icon, Text `dwc-nav__back__text`. |
| Panel title wrap | Div | | `dwc-nav__panel__title-wrap` | | Child Heading: `dwc-nav__panel__title`. |
| List <ul> | Div | `ul` | `dwc-sidebar__nav__ul` | | |
| li - link | Div | `li` | `dwc-sidebar__nav__li` | | Child WrapperLink `dwc-sidebar__nav__link` > Icon `dwc-nav__link__icon` + Text `dwc-nav__link__text`. |
| li -  slide button | Div | `li` | `dwc-sidebar__nav__li` | | Child `slide button` (Div, `dwc-sidebar__nav__btn`, attributes `role`, `tabindex`, `data-title`) > Icon, Text, chevron Icon `dwc-nav__link__icon--chevron-right`. |
| li -  dropdwon | Div | `li` | `dwc-sidebar__nav__li`, `dwc-sidebar__dropdown` | | Children: `dropdown toggle` (`dwc-sidebar__dropdown-toggle`) > Icon, Text, `button` > chevron; `dropdown content` (`dwc-sidebar__dropdown-content`) > List <ul> > li items. |
| panel footer | Div | | `dwc-sidebar__nav__panel-footer` | | Social wrapper (`dwc-social-wrapper`) with three WrapperLinks (`dwc-social`), and a Button (`dwc-hide`, `dwc-fade`). |
| mobile menu overaly | Div | | `dwc-mobile-menu-overlay` | `tabindex` `0` | |
| Sidebar Nav Codes | CodeBlock | | | | The one Code Block you edit. |

Property paths: link `content.content.link` (`{type, url}`); Text and Heading `content.content.text`; Icon `content.content.icon`; Button `content.content.text`; HtmlImg `content.content.attributes.src`; Code Block `content.content.javascript_code` and `content.content.css_code`; attributes and classes `settings.advanced.attributes` (`[{name, value}]`) and `settings.advanced.classes`.

## 3. JS options

`DWCSidebarConfig` at the top of the Code Block's `javascript_code`. `1` on, `0` off.

| Option | Template | Needs / limits | Effect |
| --- | --- | --- | --- |
| `mq` | `window.matchMedia("(max-width: 1024px)")` | Change with three CSS media queries and the JS value (build file, "Change the breakpoint") | Mobile breakpoint. |
| `offCanvasBreakpoint` | `window.matchMedia("(max-width:10024px)")` |  | Off-canvas applies at this width and below: every screen by default. |
| `enableRTL` | `0` |  | Sets `dir="rtl"` on `<html>`. The sidebar moves to the right and the whole page turns right to left. |
| `calcHeaderHeight` | `1` | Nothing reads it | No effect in 3.0.3. |
| `updateBackText` | `1` |  | Back button text becomes `back to <data-title of the target panel>`. The words "back to" are fixed in the code. |
| `autoCurrentPosition` | `1` | Skipped while collapsed | Slides to the panel holding the current page's link. A current link in a dropdown opens its dropdown. |
| `offsetHashLinkScroll` | `0` |  | Clicking a `#hash` link scrolls to its target minus the header inner wrap height. |
| `enableTopBar` | `0` | `enableOffCanvas: 0`; attribute `topbar` `"1"` | Header inner wrap becomes a full-width bar above the sidebar. Adds `dwc-topbar-enabled` to `<body>`. |
| `enableOffCanvas` | `0` | Attribute `offcanvas` `"1"` | The sidebar hides off screen and a menu button opens it, at the widths `offCanvasBreakpoint` matches. Turns off the collapsible sidebar. Adds `dwc-offcanvas`. |
| `offCanvasPushContent` | `0` | `enableOffCanvas: 1` | The open sidebar pushes the page aside. Turns off headroom. Adds `dwc-push-content`. |
| `fixedNavTrigger` | `1` | `offCanvasPushContent: 1`, desktop | The menu button stays in place while the page is pushed. Adds `dwc-nav-trigger-is-fixed`. |
| `overlayTopBar` | `0` | `enableOffCanvas: 1` | The top bar sits over the content. Adds `dwc-overlay-topbar`. |
| `mobileMenuAboveHeader` | `0` |  | The mobile and off-canvas menu opens over the top bar. Adds `dwc-mobile-menu-over`. |
| `openFirstDropDown` | `0` |  | Clicks the first dropdown toggle 600 ms after start. |
| `autoCloseDropdown` | `1` |  | A dropdown closes when focus leaves it. |
| `overlaySidebar` | `0` | `enableOffCanvas: 0` | The sidebar sits over the page content. Adds `dwc-overlay-sidebar`. |
| `enableCollapsibleSidebar` | `1` | Desktop only; off whenever `enableOffCanvas: 1` | Turns on the Collapse toggle. Adds `dwc-collapse-enabled`. |
| `collapseOnPageLoad` | `0` | `enableCollapsibleSidebar: 1` | Starts collapsed. |
| `restoreActivePanelOnExpand` | `1` | `enableCollapsibleSidebar: 1` | On expand, goes back to the panel and dropdowns that were open. |
| `saveCollapseState` | `1` | `enableCollapsibleSidebar: 1` | Saves the state in `localStorage` key `sidebarCollapsed`. |
| `hoverToExpandSidebar` | `0` | `enableCollapsibleSidebar: 1` | Expands on hover while collapsed, collapses on mouse leave. |
| `collapseAutoWidth` | `1` |  | Collapsed width from `--sidebar-panel-inline-padding`, `--sidebar-link-inline-padding` and `--sidebar-link-icon-size`. `0` uses `--sidebar-collapse-width`. Adds `dwc-auto-width`. |
| `enableTooltips` | `1` |  | Sets `data-tooltip` (the item's text) on links, buttons, dropdown toggles and social links. Shown while collapsed. |
| `debugTooltips` | `0` |  | Logs each tooltip to the console. |
| `enableHeadroom` | `1` | `enableOffCanvas` or `enableTopBar`, and not `offCanvasPushContent` | Header hides on scroll down past 200px and returns on scroll up. Adds `dwc-headroom`, `scroll-down`, `scroll-up`. |
| `reinitOnUrlChange` | `true` |  | Restarts the sidebar when the page address changes without a full load. `true`/`false`. |
| `calcTopPadding` | not in the template | `enableOffCanvas: 1`, or `enableTopBar` with `enableHeadroom` | Read by the code. Pads the first section by the header inner wrap height. Add the line to the options to use it with off-canvas on desktop. |

### Per-page options

`urlConfigMap` sits right below `DWCSidebarConfig`. The template ships it empty, with an example inside a `/* ... */` comment. Add entries outside the comment: `'/path': { option: value }`. The key is `location.pathname` without the trailing `/`; the home page is `''`. The page uses `{ ...DWCSidebarConfig, ...urlConfigMap[path] }`.

### Runtime names

* `window.DWCSidebarNavigation`: the class. `DWCSidebarNavigation.reinitialize(config)` restarts the sidebar. `new DWCSidebarNavigation(config)` replaces the running one.
* `DWCSidebarNavigation.activeInstance`: the running sidebar. `.config` holds the live options. `.reinitialize(config)` and `.cleanup()` work on it.
* `sidebar`, `DWCSidebarConfig` and `urlConfigMap` are private to the page's function and are `undefined` outside it.

## 4. Attributes

On the root section (`settings.advanced.attributes`):

| Attribute | Template | Effect |
| --- | --- | --- |
| `offcanvas` | `"0"` | `"1"` with `enableOffCanvas: 1`. Applies the off-canvas layout before the code runs. With the option `0` it breaks the layout. |
| `topbar` | `"0"` | `"1"` with `enableTopBar: 1`. Applies the top bar layout before the code runs. |
| `data-footer-scrollable` | `"true"` | The panels scroll (`overflow-y: auto`) when the menu is taller than the screen. Empty: `hidden`. |
| `data-overlap-collapsible` | empty | `"true"`: the collapsed sidebar covers the content (the content is full width). |
| `data-disable-animation` | empty | `"1"`: transitions in the sidebar, `main` and sections are `0s`. |
| `data-disable-motion-on-load` | empty | `"1"`: same as above until the code removes the attribute 300 ms after load. |
| `data-collapse` | empty | `"1"`: the sidebar is held at the collapsed width until the code removes the attribute 300 ms after load. |

On the Collapse toggle: `data-static` (`"true"`): the button stays inside the header inner wrap instead of floating at the sidebar edge.

## 5. CSS variables

In the first `:root` rule of the Code Block's `css_code`. Existing variables only. Three of them do nothing in 3.0.3: `--sidebar-tooltip-font-color` (tooltip text is always white), `--lvl-1-toggle-color-active` and `--lvl-1-icon-hover-color`.

| Variable | Template value |
| --- | --- |
| `--sidebar-width` | `min(95vw, 300px)` |
| `--sidebar-header-bg` | `gray` |
| `--sidebar-nav-bg` | `white` |
| `--sidebar-header-block-padding` | `clamp(1rem, 0.716rem + 1.211vw, 1.75rem)` |
| `--sidebar-header-inline-padding` | `var(--pad-m)` |
| `--sidebar-shadow` | `0px 0px 3px rgba(0, 0, 0, 0.75), 0px 17px 24px rgba(0, 0, 0, 0.3)` |
| `--sidebar-hamburger-color` | `white` |
| `--sidebar-close-btn-color` | `lightgray` |
| `--sidebar-link-color` | `dimgray` |
| `--sidebar-link-bg` | `initial` |
| `--sidebar-link-icon-color` | `dimgray` |
| `--sidebar-link-txt-size` | `1rem` |
| `--sidebar-link-icon-size` | `24px` |
| `--sidebar-link-inline-padding` | `1rem` |
| `--sidebar-link-block-padding` | `1rem` |
| `--sidebar-link-border-radius` | `0` |
| `--sidebar-link-underline` | `1px solid rgb(0 0 0 / 10%)` |
| `--sidebar-link-transition` | `300ms` |
| `--sidebar-link-hover-color` | `black` |
| `--sidebar-link-hover-bg` | `rgb(0 0 0 / 5%)` |
| `--sidebar-link-icon-hover-color` | `black` |
| `--sidebar-link-gap` | `1.125rem` |
| `--sidebar-dropdown-link-color` | `dimgray` |
| `--sidebar-dropdown-link-bg` | `transparent` |
| `--sidebar-dropdown-content-bg` | `rgb(0 0 0 / 5%)` |
| `--dropdown-links-underline` | `none` |
| `--sidebar-dropdown-link-hover-color` | `black` |
| `--sidebar-dropdown-links-hover-bg` | `rgb(0 0 0 / 8%)` |
| `--sidebar-dropdown-links-indent` | `15px` |
| `--sidebar-list-items-block-padding` | `1.25rem` |
| `--sidebar-list-gap` | `0` |
| `--sidebar-chevron-size` | `1rem` |
| `--sidebar-chevron-color` | `#62588f` |
| `--sidebar-social-link-color` | `dimgray` |
| `--sidebar-social-link-bg` | `initial` |
| `--sidebar-social-icon-color` | `var(--sidebar-social-link-color)` |
| `--sidebar-social-icon-size` | `var(--sidebar-link-icon-size)` |
| `--sidebar-social-link-hover-color` | `black` |
| `--sidebar-social-link-hover-bg` | `rgb(0 0 0 / 5%)` |
| `--sidebar-social-icon-hover-color` | `var(--sidebar-social-link-hover-color)` |
| `--sidebar-panel-title-size` | `1.125rem` |
| `--sidebar-panel-title-color` | `black` |
| `--sidebar-panel-title-bg` | `white` |
| `--sidebar-panel-label-color` | `orangered` |
| `--sidebar-panel-backtext-font-size` | `11px` |
| `--sidebar-panel-backtext-color` | `var(--sidebar-link-color)` |
| `--sidebar-panel-block-padding` | `clamp(0.5rem, -1.375rem + 5vh, 2rem)` |
| `--sidebar-panel-inline-padding` | `0.7rem` |
| `--sidebar-footer-top-border` | `1px solid rgb(0 0 0 / 10%)` |
| `--sidebar-footer-block-padding` | `1.25rem` |
| `--sidebar-footer-inline-padding` | `var(--sidebar-panel-inline-padding)` |
| `--sidebar-current-link-bg` | `none` |
| `--sidebar-current-link-color` | `black` |
| `--sidebar-current-link-underline` | `solid 3px orangered` |
| `--sidebar-current-link-border-radius` | `0` |
| `--sidebar-current-link-hover-bg` | `none` |
| `--sidebar-current-link-hover-color` | `black` |
| `--sidebar-collapse-width` | `80px` |
| `--sidebar-tooltip-font-size` | `10px` |
| `--sidebar-tooltip-font-color` | `white` |
| `--sidebar-tooltip-bg` | `black` |
| `--sidebar-tooltip-radius` | `0.5em` |
| `--sidebar-tooltip-inline-padding` | `1em` |
| `--sidebar-tooltip-block-padding` | `0.5em` |
| `--sidebar-backdrop-overlay-bg` | `white` |
| `--sidebar-backdrop-overlay-opacity` | `0.5` |
| `--skip-link-color` | `white` |
| `--skip-link-background` | `black` |
| `--sidebar-transition` | `500ms` |
| `--sidebar-ttf` | `cubic-bezier(1, 0, 0.25, 1)` |
| `--pad-m` | `1.25rem` |
| `--pad-s` | `0.75rem` |
| `--pad-xs` | `0.5rem` |
| `--sidebar-focus-outline-color` | `black` |
| `--sidebar-focus-outline-width` | `2px` |
| `--sidebar-focus-outline-offset` | `4px` |
| `--sidebar-collapse-ttf` | `cubic-bezier(0.1, 0.55, 0.35, 1)` |
| `--sidebar-opacity-transition` | `500ms 200ms` |
| `--lvl-2-indent` | `var(--sidebar-dropdown-links-indent)` |
| `--lvl-3-indent` | `var(--sidebar-dropdown-links-indent)` |
| `--lvl-1-toggle-bg-active` | `var(--sidebar-link-hover-bg)` |
| `--lvl-2-toggle-bg-active` | `var(--sidebar-link-hover-bg)` |
| `--lvl-3-toggle-bg-active` | `var(--sidebar-link-hover-bg)` |
| `--lvl-1-content-bg` | `var(--sidebar-dropdown-content-bg)` |
| `--lvl-2-content-bg` | `var(--sidebar-dropdown-content-bg)` |
| `--lvl-3-content-bg` | `var(--sidebar-dropdown-content-bg)` |
| `--lvl-1-toggle-color-active` | `var(--sidebar-link-color)` |
| `--lvl-2-toggle-color-active` | `var(--sidebar-link-color)` |
| `--lvl-3-toggle-color-active` | `var(--sidebar-link-color)` |
| `--lvl-1-icon-color` | `var(--sidebar-link-icon-color)` |
| `--lvl-2-icon-color` | `var(--sidebar-link-icon-color)` |
| `--lvl-3-icon-color` | `var(--sidebar-link-icon-color)` |
| `--lvl-1-icon-hover-color` | `var(--sidebar-link-icon-hover-color)` |
| `--lvl-2-icon-hover-color` | `var(--sidebar-link-icon-hover-color)` |
| `--lvl-3-icon-hover-color` | `var(--sidebar-link-icon-hover-color)` |
| `--lvl-2-icon-size` | `1.8rem` |
| `--lvl-3-icon-size` | `1.8rem` |

Related, outside `:root`: `.dwc-auto-width` sets `--icon-size-multiplier` (`1`) and computes `--sidebar-collapse-width`. `:root`/`[dir="rtl"]` set `--dir-direction`, `--dir-active-rotation` and `--dir-rotation`: do not change them.

## 6. Classes

### Helper classes

* `dwc-hide`: hidden while the sidebar is collapsed. With `dwc-fade` it fades out.

### On `<body>`

| Class | When |
| --- | --- |
| `show-nav` | The code has run and the sidebar is ready, 300 ms after load. |
| `dwc-mobile` | Below `mq`. |
| `dwc-slide-nav-open` | The mobile or off-canvas menu is open. `dwc-no-scroll` comes with it. |
| `dwc-collapse-enabled` | The collapsible sidebar is on. |
| `dwc-auto-width` | `collapseAutoWidth` is on. |
| `dwc-collapse-sidebar` | Collapsed. `dwc-is-collapsed` follows 500 ms later. |
| `dwc-offcanvas` | Off-canvas is active. |
| `dwc-push-content` | Push content is active. |
| `dwc-nav-trigger-is-fixed` | The menu button is fixed while the page is pushed. |
| `dwc-topbar-enabled` | The top bar is on. |
| `dwc-headroom` | Headroom is on. `scroll-down` or `scroll-up` shows the direction. |
| `dwc-overlay-sidebar`, `dwc-overlay-topbar`, `dwc-mobile-menu-over` | The matching option is on. |
| `hasHeaderHeight` | The code measured the header. |

The link to the current page gets `dwc-current-menu-item`.

## 7. Code Block fields

| Field | Holds |
| --- | --- |
| `javascript_code` | Options, `urlConfigMap`, then the engine. |
| `css_code` | The `:root` variables, then the engine CSS. Breakpoint media queries: `@media(max-width:1024px)`, `@media (min-width: 1025px)`, `@media (max-width:1024px)`. |
| `php_code` | A leftover comment. Leave it. |
| `disable_builder_label` | `true`. |
