---
icon: code
---

# Page Transitions & JavaScript

You don't need this page to use the sidebar. It's for when your own JavaScript has to restart the sidebar or change its options while the page is open.

***

## What your code can reach

The sidebar's code runs inside a function, so most of its names are private. Only one name is public:

| Name | What it is |
| --- | --- |
| `DWCSidebarNavigation` | The sidebar's class. It is on `window`. |
| `DWCSidebarNavigation.activeInstance` | The sidebar that is running now. |

These names are **not** available to your code, and give you an error or `undefined`: `sidebar`, `DWCSidebarConfig` and `urlConfigMap`. Change your options in the **Sidebar Nav Codes** Code Block instead. See [Sidebar Options](../sidebar-options.md).

### Where to put your code

Your code must run after the sidebar has started. Put it in one of these places:

* **A Code Block placed below Sidebar Nav Codes** in the sidebar template.
* **Your site's footer scripts.**

Don't put it in **Sidebar Nav Codes**.

***

## Restart the sidebar

```js
DWCSidebarNavigation.activeInstance.reinitialize();
```

Use it after your code adds or replaces menu items, for example after loading content with AJAX. The sidebar finds its elements again and starts over.

### Restart with other options

```js
DWCSidebarNavigation.activeInstance.reinitialize({ enableCollapsibleSidebar: 0, enableOffCanvas: 1 });
```

* The options you pass are added to the options in the **Sidebar Nav Codes** Code Block. Every other option keeps its value from there.
* Each call starts again from those options, so options from an earlier call are gone. Pass every change you want, every time.
* Per-page options from `urlConfigMap` are not added for you. Pass them yourself if you need them.

`DWCSidebarNavigation.reinitialize({ ... })` does the same from the class, without needing the running sidebar.

## Stop the sidebar

```js
DWCSidebarNavigation.activeInstance.cleanup();
```

This removes the sidebar's classes and event listeners from the page. To start it again, call `DWCSidebarNavigation.reinitialize()`.

## One sidebar at a time

Only one sidebar runs on a page. `new DWCSidebarNavigation(options)` stops the running sidebar before it starts a new one. To change a running sidebar, use `reinitialize` instead.

***

## Page transitions

Some plugins load the next page without a full reload, for example AJAX page transitions. The sidebar handles this itself: with the `reinitOnUrlChange` option on (the template value), it restarts every time the page address changes. See [Sidebar Options](../sidebar-options.md#page-transitions).

If the sidebar still stops working after a transition, restart it from your plugin's "after the page changes" setting. Add this code:

```js
if (window.DWCSidebarNavigation) DWCSidebarNavigation.reinitialize();
```
