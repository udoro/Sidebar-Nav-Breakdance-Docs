---
icon: wrench
---

# Troubleshooting

| Problem | What to do |
| --- | --- |
| The sidebar doesn't show on the site | Check the header template's conditions: they must cover this page. Then clear your site's cache. |
| A slide button doesn't open its panel | The button's `data-title` and the panel's `data-title` must match exactly, including capital letters and spaces. See [Naming panels](building-the-navigation.md#naming-panels). |
| A slide button opens the wrong panel | Two panels have the same `data-title`. Give each panel its own name. |
| The layout breaks between two screen widths | The breakpoint was changed in one place only. Change it in all four. See [Change the breakpoint](sidebar-options.md#change-the-breakpoint). |
| After turning on off-canvas or the top bar, the sidebar hides and a bar stretches across the top | The `offcanvas` or `topbar` attribute doesn't match the option. Set the attribute to `1` when the option is `1`, and to `0` when it is `0`. See [Sidebar attributes](attributes-and-classes.md#sidebar-attributes). |
| A red message tells logged-in users to set `offcanvas` to `0` | The `offcanvas` attribute is `1` but `enableOffCanvas` is `0`. Make them match. |
| The sidebar flashes while the page loads | Set the `offcanvas` or `topbar` attribute to match its option. If the sidebar starts collapsed, also try `data-collapse` set to `1`. |
| The top bar doesn't hide on scroll | Headroom needs `enableOffCanvas` or `enableTopBar` set to `1`, and doesn't work with `offCanvasPushContent`. See [Headroom and scrolling](sidebar-options.md#headroom-and-scrolling). |
| There's no collapse button | Set `enableCollapsibleSidebar` to `1`. The collapsible sidebar works on desktop only, and not when `enableOffCanvas` is `1`. |
| Icons are cut off when collapsed | The collapsed width doesn't fit your icons. See [Collapsed width](styling.md#collapsed-width). |
| A tooltip has the wrong text color | The tooltip text is always white in 3.0.3. `--sidebar-tooltip-font-color` doesn't change it. Change `--sidebar-tooltip-bg` to keep the text easy to read. |
| The sidebar stops working after a page transition | See [Page Transitions & JavaScript](guides/javascript-api.md). |
| `sidebar` or `DWCSidebarConfig` is not defined in my own code | They are not available to other scripts. See [Page Transitions & JavaScript](guides/javascript-api.md). |

## Keyboard and screen readers

The sidebar works with the keyboard: Tab moves through the menu, Enter opens a panel or dropdown, and Escape closes it. If you change the colors, test the menu with the keyboard and a screen reader. Keep the focus outline easy to see. See [Focus outline](styling.md#focus-outline).
