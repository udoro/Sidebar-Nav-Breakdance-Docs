---
icon: tags
---

# Attributes & Classes

## Sidebar attributes

These attributes are on the **Sidebar &lt;header&gt;** section, the top element of the template. To change one, see [Change an attribute](README.md#change-an-attribute).

| Attribute | Template value | What it does |
| --- | --- | --- |
| `offcanvas` | `0` | Set it to `1` when the `enableOffCanvas` option is `1`. It stops the layout from flashing while the page loads. Keep it in step with the option. |
| `topbar` | `0` | Set it to `1` when the `enableTopBar` option is `1`. It stops the layout from flashing while the page loads. Keep it in step with the option. |
| `data-footer-scrollable` | `true` | With `true`, the sidebar scrolls when the menu is longer than the screen. Clear the value to turn the scrolling off. |
| `data-overlap-collapsible` | empty | Set it to `true` and the collapsible sidebar covers the page content instead of pushing it aside. |
| `data-disable-animation` | empty | Set it to `1` to turn off every slide and fade in the sidebar. |
| `data-disable-motion-on-load` | empty | Set it to `1` to turn off the sidebar's motion while the page loads. The template removes this attribute 300 ms after the page loads. |
| `data-collapse` | empty | Set it to `1` to hold the sidebar at its collapsed width while the page loads. The template removes this attribute 300 ms after the page loads. |

{% hint style="warning" %}
**Keep `offcanvas` and `topbar` in step with their options.** If `offcanvas` is `1` and `enableOffCanvas` is `0`, the sidebar breaks: it hides off the screen and the bar stretches across the top. Logged-in users also see a red message on the page that tells them to set `offcanvas` back to `0`.

If the option is `1` and the attribute is `0`, the sidebar works, but it can flash while the page loads.
{% endhint %}

## Collapse toggle attribute

This attribute is on the **Collapse toggle** element.

| Attribute | Template value | What `true` does |
| --- | --- | --- |
| `data-static` | empty | The button stays where it sits in the **header inner wrap**, instead of floating at the edge of the sidebar. |

***

## Helper classes

Add these classes to any element inside the sidebar.

| Class | What it does |
| --- | --- |
| `dwc-hide` | Hides the element while the sidebar is collapsed. The template's panel footer **Button** uses it. |
| `dwc-fade` | With `dwc-hide`, the element fades out instead of disappearing at once. |

***

## Classes on the page

The sidebar adds classes to `<body>`, so your own CSS can change things in each state.

| Class on `<body>` | When it's there |
| --- | --- |
| `show-nav` | The sidebar's code has run and the sidebar is ready. It is added 300 ms after the page loads. |
| `dwc-mobile` | Below the breakpoint. |
| `dwc-slide-nav-open` | The mobile or off-canvas menu is open. |
| `dwc-collapse-enabled` | The collapsible sidebar is on. |
| `dwc-collapse-sidebar` | The sidebar is collapsed. |
| `dwc-is-collapsed` | The sidebar has finished collapsing. It comes 500 ms after `dwc-collapse-sidebar`. |
| `dwc-offcanvas` | Off-canvas mode is active. |
| `dwc-push-content` | Off-canvas push content is active. |
| `dwc-topbar-enabled` | The top bar is on. |
| `dwc-headroom` | Headroom is on. `scroll-down` and `scroll-up` show which way the visitor last scrolled. |

The link to the current page gets the `dwc-current-menu-item` class.

### Example: a different logo when collapsed

A wide logo doesn't fit the collapsed sidebar. You can show a small logo in its place.

1. Put both logos in one element with the class `logo-wrap`. Give the wide logo the class `default-logo`, and the small one `alt-logo`.
2. Add this CSS to your site, for example in a Code Block below the sidebar:

```css
.logo-wrap {
  position: relative;
}

.logo-wrap img {
  position: absolute;
}

.default-logo {
  opacity: 1;
}

.alt-logo {
  opacity: 0;
}

.dwc-collapse-sidebar .default-logo {
  opacity: 0;
}

.dwc-collapse-sidebar .alt-logo {
  opacity: 1;
}
```

Both logos sit in the same spot, and only one shows at a time. Give `.logo-wrap` a height that fits your logo, because both images are taken out of the layout.
