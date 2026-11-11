---
icon: clock-rotate-left
---

# Changelog

You'll find every version's template in your Gumroad library.

## 3.1

### New

- **Split dropdowns.** Set the `data-partition-dropdown` attribute to `true` and each dropdown row splits in two: the label, and the chevron in its own box. Only the box opens the dropdown, so the label can be a link. See [Split dropdowns](building-the-navigation.md#split-dropdowns).
- **New icons.** The template's icons are now [Phosphor Icons](https://phosphoricons.com), regular style. The Twitter link is now X.

### Improved

- **Collapsible by default.** The template now comes with the collapsible sidebar on: the `enableCollapsibleSidebar` option is `1`. Set it to `0` if you don't want it. A sidebar you already built keeps its own setting.
- **Nested dropdowns.** They keep their full width now, instead of getting narrower at each level.

### Fixed

- **The admin bar.** When you're logged in, WordPress's admin bar no longer covers the top of the sidebar, and the mobile menu's first items are no longer hidden behind the header.
- **Blocked cookies.** The sidebar now works for visitors whose browser blocks cookies. Before, it didn't load at all.
- **The collapsible sidebar after a resize.** When the window changes between desktop and mobile size, the collapsible sidebar keeps working, and its toggle no longer shows in the mobile menu bar. Before, it needed a page reload.
- **The top bar on phones.** The page now starts right below the menu bar. Before, it sat a little too high until you resized the window.
- **Links in the mobile menu.** A link to a section on the same page now closes the mobile menu in every layout, not only in off-canvas.
- **Colors that did nothing.** These variables work now: `--lvl-1-toggle-color-active` (the text of an open level 1 dropdown), `--sidebar-dropdown-link-color` and `--sidebar-dropdown-link-hover-color` (the text of dropdown links), `--sidebar-social-link-hover-bg` (the background of a social link on hover), `--sidebar-tooltip-font-color` (the text of a tooltip) and `--lvl-1-icon-hover-color` (the icon of a level 1 dropdown on hover). If you never changed them, nothing looks different.

## Earlier versions

For the full changelog, see the [product on Gumroad](https://designwithcracka.gumroad.com/l/ResponsiveSidebarmulti-levelSlideNavigationTemplateforBREAKDANCEBUILDER).
