---
icon: palette
---

# Styling

You style the sidebar with CSS variables. Change them in the **CSS** field of the **Sidebar Nav Codes** Code Block, inside the `:root { }` rule at the top.

The **Template value** column is what each variable is set to when you paste the template.

## How to change a variable

1. In the builder, select **Sidebar Nav Codes** in the Structure panel.
2. Open its **CSS** field.
3. Find the variable inside `:root` and change its value.
4. Save.

Change the value only. Leave the variable name, the colon and the semicolon as they are.

{% hint style="info" %}
Give a length of zero a unit, for example `0px`, not `0`. The collapsed width is worked out from `--sidebar-panel-inline-padding`, `--sidebar-link-inline-padding` and `--sidebar-link-icon-size`, and a bare `0` breaks that sum.
{% endhint %}

Don't change the rules under `:root`. They are part of the template. To style something the variables don't cover, add your own CSS in a separate place, such as a Code Block below the sidebar or your site's custom CSS. See [Your own CSS](#your-own-css).

---

## Sidebar

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-width` | `min(95vw, 300px)` | Width of the sidebar. Also the width of the off-canvas menu and the mobile menu. |
| `--sidebar-header-bg` | `gray` | Background of the Header inner wrap, the area with the logo and buttons. In top bar and off-canvas modes it also colors the full-width bar. |
| `--sidebar-nav-bg` | `white` | Background of the sidebar and of every panel. |
| `--sidebar-header-block-padding` | `clamp(1rem, 0.716rem + 1.211vw, 1.75rem)` | Space above and below the logo and buttons in the Header inner wrap. |
| `--sidebar-header-inline-padding` | `var(--pad-m)` | Space left and right of the logo and buttons in the Header inner wrap. |
| `--sidebar-shadow` | `0px 0px 3px rgba(0, 0, 0, 0.75), 0px 17px 24px rgba(0, 0, 0, 0.3)` | Shadow around the sidebar. |

## Menu button and close button

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-hamburger-color` | `white` | Color of the menu button lines (the hamburger). |
| `--sidebar-close-btn-color` | `lightgray` | Color of the close button in the open mobile and off-canvas menu. |

## Links

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-link-color` | `dimgray` | Text color of a link. |
| `--sidebar-link-bg` | `initial` | Background of a link. |
| `--sidebar-link-icon-color` | `dimgray` | Color of a link icon. |
| `--sidebar-link-txt-size` | `1rem` | Font size of a link. |
| `--sidebar-link-icon-size` | `24px` | Size of a link icon. Also used to work out the collapsed width. |
| `--sidebar-link-inline-padding` | `1rem` | Space left and right inside a link. Also used to work out the collapsed width. |
| `--sidebar-link-block-padding` | `1rem` | Space above and below the text inside a link. |
| `--sidebar-link-border-radius` | `0` | Rounded corners of a link. |
| `--sidebar-link-underline` | `1px solid rgb(0 0 0 / 10%)` | The line under each menu item. |
| `--sidebar-link-transition` | `300ms` | How long the hover change takes. |
| `--sidebar-link-gap` | `1.125rem` | Space between a link icon and its text. |
| `--sidebar-link-hover-color` | `black` | Text color of a link on hover. |
| `--sidebar-link-hover-bg` | `rgb(0 0 0 / 5%)` | Background of a link on hover. Dropdown buttons use it when open. |
| `--sidebar-link-icon-hover-color` | `black` | Icon color of a link on hover. |

## Current page link

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-current-link-bg` | `none` | Background of the link to the page you are on. |
| `--sidebar-current-link-color` | `black` | Text color of that link. |
| `--sidebar-current-link-underline` | `solid 3px orangered` | The line under that link. |
| `--sidebar-current-link-border-radius` | `0` | Rounded corners of that link. |
| `--sidebar-current-link-hover-bg` | `none` | Background of that link on hover. |
| `--sidebar-current-link-hover-color` | `black` | Text color of that link on hover. |

## Dropdowns

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-dropdown-link-color` | `dimgray` | Text color of a link inside a dropdown. |
| `--sidebar-dropdown-link-bg` | `transparent` | Background of a link inside a dropdown. |
| `--sidebar-dropdown-content-bg` | `rgb(0 0 0 / 5%)` | Background of an open dropdown list. The level variables below start from this value. |
| `--dropdown-links-underline` | `none` | The border around each item inside a dropdown list. |
| `--sidebar-dropdown-link-hover-color` | `black` | Text color of a dropdown link on hover. |
| `--sidebar-dropdown-links-hover-bg` | `rgb(0 0 0 / 8%)` | Background of a dropdown link on hover. |
| `--sidebar-dropdown-links-indent` | `15px` | How far each dropdown level moves to the right. The level 2 and 3 indents start from this value. |
| `--sidebar-list-items-block-padding` | `1.25rem` | Space above and below a menu list. |
| `--sidebar-list-gap` | `0` | Space between the items of a menu list. It also spaces the buttons in a Panel header and the social links. |
| `--sidebar-chevron-size` | `1rem` | Size of the chevron arrow on slide buttons and dropdowns. |
| `--sidebar-chevron-color` | `#62588f` | Color of the chevron arrow. |

## Panels and Back button

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-panel-title-size` | `1.125rem` | Font size of the panel title. |
| `--sidebar-panel-title-color` | `black` | Color of the panel title. |
| `--sidebar-panel-title-bg` | `white` | Background behind the panel title. |
| `--sidebar-panel-label-color` | `orangered` | Color of the name labels that show in the builder on panels and buttons. Visitors never see them. |
| `--sidebar-panel-backtext-font-size` | `11px` | Font size of the Back button text. |
| `--sidebar-panel-backtext-color` | `var(--sidebar-link-color)` | Color of the Back button text. |
| `--sidebar-panel-block-padding` | `clamp(0.5rem, -1.375rem + 5vh, 2rem)` | Space above and below the content of a panel. |
| `--sidebar-panel-inline-padding` | `0.7rem` | Space left and right of the content of a panel. Also used to work out the collapsed width. |

## Panel footer and social links

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-footer-top-border` | `1px solid rgb(0 0 0 / 10%)` | The line above the Panel footer. |
| `--sidebar-footer-block-padding` | `1.25rem` | Space above and below the Panel footer content. |
| `--sidebar-footer-inline-padding` | `var(--sidebar-panel-inline-padding)` | Space left and right of the Panel footer content. |
| `--sidebar-social-link-color` | `dimgray` | Text color of a social link. |
| `--sidebar-social-link-bg` | `initial` | Background of a social link. |
| `--sidebar-social-icon-color` | `var(--sidebar-social-link-color)` | Color of a social icon. |
| `--sidebar-social-icon-size` | `var(--sidebar-link-icon-size)` | Size of a social icon. |
| `--sidebar-social-link-hover-color` | `black` | Text color of a social link on hover. |
| `--sidebar-social-link-hover-bg` | `rgb(0 0 0 / 5%)` | Background of a social link on hover. |
| `--sidebar-social-icon-hover-color` | `var(--sidebar-social-link-hover-color)` | Color of a social icon on hover. |

## Collapsed sidebar and tooltips

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-collapse-width` | `80px` | Width of the collapsed sidebar. It only applies when `collapseAutoWidth` is `0`. |
| `--sidebar-tooltip-font-size` | `10px` | Font size of a tooltip. |
| `--sidebar-tooltip-font-color` | `white` | Not used in 3.0.3. Changing it does nothing. Tooltip text is always white. |
| `--sidebar-tooltip-bg` | `black` | Background of a tooltip. |
| `--sidebar-tooltip-radius` | `0.5em` | Rounded corners of a tooltip. |
| `--sidebar-tooltip-inline-padding` | `1em` | Space left and right inside a tooltip. |
| `--sidebar-tooltip-block-padding` | `0.5em` | Space above and below the text inside a tooltip. |

## Backdrop and skip links

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-backdrop-overlay-bg` | `white` | Color of the layer behind the open mobile and off-canvas menu. |
| `--sidebar-backdrop-overlay-opacity` | `0.5` | How solid that layer is. `0` is clear, `1` is solid. |
| `--skip-link-color` | `white` | Text color of the skip links that show when you tab into the page. |
| `--skip-link-background` | `black` | Background of the skip links. |

## Focus outline

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-focus-outline-color` | `black` | Color of the outline around the item that has keyboard focus. |
| `--sidebar-focus-outline-width` | `2px` | Width of that outline. |
| `--sidebar-focus-outline-offset` | `4px` | Gap between that outline and the item. |

## Motion

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--sidebar-transition` | `500ms` | How long panels slide and the sidebar opens. |
| `--sidebar-ttf` | `cubic-bezier(1, 0, 0.25, 1)` | The easing curve of that motion. |
| `--sidebar-collapse-ttf` | `cubic-bezier(0.1, 0.55, 0.35, 1)` | The easing curve of the collapse and expand motion. |
| `--sidebar-opacity-transition` | `500ms 200ms` | Duration and delay of the fade when text hides or shows. |

## General spacing

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--pad-m` | `1.25rem` | Medium space. Used for the left and right padding of the Header inner wrap and in the skip links. |
| `--pad-s` | `0.75rem` | Small space. Used inside the panel title and the Home button. |
| `--pad-xs` | `0.5rem` | Extra small space. Used inside the panel title and the skip links. |

## Dropdown levels

| Variable | Template value | What it sets |
| --- | --- | --- |
| `--lvl-1-toggle-bg-active` | `var(--sidebar-link-hover-bg)` | Background of a level 1 dropdown button while it is open. |
| `--lvl-1-content-bg` | `var(--sidebar-dropdown-content-bg)` | Background of a level 1 dropdown list. |
| `--lvl-1-toggle-color-active` | `var(--sidebar-link-color)` | Not used in 3.0.3. Changing it does nothing. |
| `--lvl-1-icon-color` | `var(--sidebar-link-icon-color)` | Icon color at level 1. |
| `--lvl-1-icon-hover-color` | `var(--sidebar-link-icon-hover-color)` | Not used in 3.0.3. Changing it does nothing. |
| `--lvl-2-toggle-bg-active` | `var(--sidebar-link-hover-bg)` | Background of a level 2 dropdown button while it is open. |
| `--lvl-2-content-bg` | `var(--sidebar-dropdown-content-bg)` | Background of a level 2 dropdown list. |
| `--lvl-2-toggle-color-active` | `var(--sidebar-link-color)` | Text color of a level 2 dropdown button while it is open. |
| `--lvl-2-icon-color` | `var(--sidebar-link-icon-color)` | Icon color at level 2. |
| `--lvl-2-icon-hover-color` | `var(--sidebar-link-icon-hover-color)` | Icon color at level 2 on hover. |
| `--lvl-3-toggle-bg-active` | `var(--sidebar-link-hover-bg)` | Background of a level 3 dropdown button while it is open. |
| `--lvl-3-content-bg` | `var(--sidebar-dropdown-content-bg)` | Background of a level 3 dropdown list. |
| `--lvl-3-toggle-color-active` | `var(--sidebar-link-color)` | Text color of a level 3 dropdown button while it is open. |
| `--lvl-3-icon-color` | `var(--sidebar-link-icon-color)` | Icon color at level 3. |
| `--lvl-3-icon-hover-color` | `var(--sidebar-link-icon-hover-color)` | Icon color at level 3 on hover. |
| `--lvl-2-indent` | `var(--sidebar-dropdown-links-indent)` | How far level 2 moves to the right. |
| `--lvl-3-indent` | `var(--sidebar-dropdown-links-indent)` | How far level 3 moves to the right. |
| `--lvl-2-icon-size` | `1.8rem` | Icon size at level 2. |
| `--lvl-3-icon-size` | `1.8rem` | Icon size at level 3. |

---

## Collapsed width

With `collapseAutoWidth` on (the template value), the collapsed width is worked out for you:

```
(--sidebar-panel-inline-padding x 2) + (--sidebar-link-inline-padding x 2) + (--sidebar-link-icon-size x --icon-size-multiplier)
```

`--icon-size-multiplier` starts at `1`. If your icons look cut off or have too much space when collapsed, change it. Divide the icon's real width (check it with your browser's inspector) by `--sidebar-link-icon-size`. It is set on the `.dwc-auto-width` rule, a few lines below `:root`.

To set the width yourself, set `collapseAutoWidth` to `0` in [Sidebar Options](sidebar-options.md) and change `--sidebar-collapse-width`.

## Your own CSS

Put your own CSS outside the **Sidebar Nav Codes** Code Block, so a new version of the template doesn't remove it. Use the classes in [Attributes & Classes](attributes-and-classes.md#classes-on-the-page) to style each state.

* **Desktop only:** start the rule with `body:not(.dwc-mobile)`.
* **Mobile only:** start the rule with `body.dwc-mobile`.
* **Collapsed only:** start the rule with `body.dwc-collapse-sidebar`.
