---
icon: sparkles
---

# AI Skills Build Reference

## START HERE

The entry file sent you here because you are on the **build path**. Read this file in full, then work through the steps in order.

### 0. Read this file first

1. Read every line before your first Breakdance write. If a read returns a truncation notice, continue with `offset`/`limit` until you reach the last line.
2. State in chat: `"Skill file read: lines 1-[N] of [N], complete."` with the real line count.

### 1. Before you start

**Session type.** Search upward from this file's folder for `SIDEBAR NAV BREAKDANCE/sidebar-nav-dev-context.md`, checking each ancestor in turn. Found: **developer session**, read it silently. Not found: **user session**.

**User session only.** Look for `sidebar-nav-breakdance-user-context.md` in this file's folder. If it exists, read it silently. If not, create it with the structure below and tell the user you created it.

```md
# Sidebar Nav Breakdance User Context

## Preferences


## Saved Layouts


## Session Notes

```

At the end of a user session, propose additions to it (the entry file's "Ask before you write" applies). A saved preference in the active context file wins over a default in this file. When you apply one, tell the user.

**Working directory.** Make a working subdirectory for this task and keep every scratch file in it (tree snapshots, code fields, scripts). Delete it at the end, except any backup you were told to keep. Use `node` for scripting and parsing. Never `python` or `jq`. Write any script that contains a backslash (a regular expression, for example) with your file-writing tool, not with a shell heredoc or `node -e`: shells strip the backslashes and the script then runs wrongly without an error.

**Timestamp.** Run `date +%s` before you start work and save the value in your working directory.

### 2. Connect, find the header, check the setup

Follow "Is the site connected" and "Find the header" in the entry file.

**No header:** ask the user to paste the template and do the installation steps (https://design-with-cracka.gitbook.io/sidebarnavbreakdance/getting-started), then start again. Never build a sidebar from Breakdance elements, and never paste the template yourself.

**Setup check**, once per session, from the tree you already read:

* The root section's `settings.advanced.attributes` has `offcanvas` and `topbar`, and each matches its option in the Code Block: `offcanvas` `"1"` exactly when `enableOffCanvas` is `1`, `topbar` `"1"` exactly when `enableTopBar` is `1`. If not, tell the user, and offer to fix it (Operations, "Change an attribute").
* The header's template conditions cover the pages the user cares about. You cannot read them with the tools above: ask the user, or fetch a published page and look for `id="dwc_header"` in the HTML.

**Probe the write path** before the first real write of the session. The sidebar's elements are older element types than the ones `breakdance-get-element-slugs` lists, so a write can be refused.

1. Read one value you will change anyway.
2. Send `breakdance-edit-post` with an `update` operation that sets that same value.
3. Read the tree back and compare.

Accepted and unchanged: carry on. Refused, or something else changed: stop writing. Give the user the builder steps for the whole task (section 5 lists them) and say why.

### 3. Scope and confirmation gate

Before any write that changes structure or look, ask the user in **one** question batch:

* **(a) Adjust what is there** (keep the menu, change look or behavior), or **(b) rebuild** (remove items and build new ones).
* **Behavior words.** "Collapsible" (shrinks to icons on desktop), "off-canvas" (hidden behind a menu button on every screen), "top bar" (a bar above the sidebar), "mobile menu" (always there below the breakpoint). If the brief uses one of these loosely, ask which it means.
* **Class names.** If you will create new classes, read the site's class prefix with `breakdance-site-info` (`css_prefix`) and propose two or three base names with it. Let the user pick or give their own. Never invent and apply one.
* **Unclear phrases.** List every phrase in the brief with more than one technical reading and resolve them in the same batch.
* **Screenshots.** If the user gives design screenshots, ask the browser zoom and window width each was taken at.

**Before option (b):** save the current `javascript_code`, `css_code` and the tree to your working directory, and tell the user those files are the restore point. Do not remove anything until the user confirms.

To undo, give the user the old value from your saved file and the builder steps to put it back. Never replace the whole header.

### 4. Order of tools

Use the first tier that can do the job. Name the tier in chat before each write.

1. **JS option** in the Code Block. Reference section 3.
2. **CSS variable** in the Code Block. Reference section 5.
3. **Attribute** on the root section or Collapse toggle. Reference section 4.
4. **Element settings**, for menu items and content you build.
5. **Custom CSS**, only when nothing above covers it. Say in chat which option, variable or attribute you checked and why it does not cover the request.

***

## 5. Operations

Before the first call of each tool in a session, read its input schema from the tool list, and follow the schema over this file where they differ. Before `breakdance-edit-post` on an element, call `breakdance-get-element-schemas` for that element's type when it returns one. A type it reports as `missing` has no schema: the probe in section 2 decides whether you may write to it.

### Read the tree

`breakdance-get-post-tree` with the header's `post_id`. The response is about 175 KB because of the Code Block: it is saved to a file. Parse that file with `node`, instead of reading it into the chat. Re-read before every write that depends on the current state.

### Write an element

`breakdance-edit-post` with `post_id` and `operations`. An `update` operation merges `properties` into the element: send only the keys you change. The operations in one call are applied together.

Read the tree after the write. Confirm the changed value equals your expected text exactly, and that nothing else changed.

### Change a JS option

1. Take the Code Block's `content.content.javascript_code` from the tree.
2. Replace the exact text of the one option line with its indent and line break, for example `\n    enableOffCanvas: 0,\n` with `\n    enableOffCanvas: 1,\n`. Confirm the old text occurs exactly once. Keep comments and spacing.
3. Write the whole `javascript_code` back with an `update` operation.

If the option is `enableOffCanvas` or `enableTopBar`, change the matching attribute in the same pass (see "Change an attribute").

Breakpoint options keep their form: `window.matchMedia("(max-width: 991px)")`. `reinitOnUrlChange` takes `true` or `false`. Never change `mq` alone (see "Change the breakpoint").

**Builder steps** to give the user: select the Code Block `Sidebar Nav Codes`, open its JavaScript field, change the number on that line, save.

### Change a CSS variable

Same as a JS option, in `content.content.css_code`: replace the one `--name: value;` line inside the first `:root`. Existing variables only. Give a zero length a unit (`0px`): the collapsed width is a `calc()` over `--sidebar-panel-inline-padding`, `--sidebar-link-inline-padding` and `--sidebar-link-icon-size`, and a bare `0` breaks it.

**Builder steps:** the same Code Block, its CSS field.

### Per-page options

Add entries to `urlConfigMap` outside its `/* ... */` comment. Key: the page path without domain and trailing `/`; the home page is `''`. Only the options that change. Attributes are not per page: see section 7.

### Change an attribute

In the element's `settings.advanced.attributes` array, change the `value` of the row with that `name`. Send the whole array with every row. Values: `offcanvas` and `topbar` take `"0"` or `"1"`. `data-footer-scrollable`, `data-overlap-collapsible` and `data-static` take `"true"`. `data-disable-animation`, `data-disable-motion-on-load` and `data-collapse` take `"1"`. Empty is off.

**Builder steps:** select the element, open Advanced, then Attributes, change the Value.

### Change a link, text or icon

* Link: the link wrapper (class `dwc-sidebar__nav__link`) inside the `li`: `content.content.link` (`{ "type": "url", "url": "..." }`).
* Text: the Text element with `dwc-nav__link__text`: `content.content.text`.
* Icon: the Icon element with `dwc-nav__link__icon`: `content.content.icon`.
* Panel title: the Heading with `dwc-nav__panel__title`: `content.content.text`.

Copy the value shape from an existing element of the same kind in the tree.

### Add a menu item

1. Pick an existing item of the same kind (reference section 2).
2. `duplicate` it with `breakdance-edit-post`. The copy gets new IDs and sits right after the original.
3. Read the tree and find the copy. Change its text and link, and for a slide button its `data-title`.
4. `move` it to the position the user wants, under the target **List &lt;ul&gt;**.

Do not `insert` the sidebar's element types: the server refuses them.

**Builder steps:** duplicate the item, change its text and link, drag it into place.

### Add a slide panel

1. `duplicate` an existing **Slide Panel**, then `move` the copy directly under **Nav**. Never inside another panel. Keep `dwc-slide-right` in its classes.
2. Set its `data-title` to a readable, unique name. Visitors see it as "back to <name>".
3. Set its panel title Heading `text`, and build its list from duplicated items.
4. Duplicate an **li - slide button** where the user wants it. Set the inner slide button's `data-title` to the panel's name, exactly.

A panel's depth comes from the slide button that opens it. Every panel stays a direct child of Nav.

### Add a dropdown inside a dropdown

`duplicate` an **li - dropdwon**, then `move` the copy into another dropdown's **dropdown content > List &lt;ul&gt;**. Level classes and level variables (`--lvl-2-*`, `--lvl-3-*`) apply on their own.

### Remove a menu element

`delete` removes the element and everything inside it. Before removing more than one, list them to the user and wait for agreement. Never remove the Home panel, the Code Block, the header inner wrap, the trigger wrapper or the mobile menu overlay.

### Change the breakpoint

Four edits, all in the Code Block, in one go. Use the user's widths; the desktop width is the mobile width + 1.

1. `javascript_code`: `mq` to `window.matchMedia("(max-width: <mobile>px)")`.
2. `css_code`: `@media (min-width: 1025px)` to `@media (min-width: <desktop>px)`.
3. `css_code`: `@media(max-width:1024px)` (no space after `@media`) to `@media(max-width:<mobile>px)`.
4. `css_code`: `@media (max-width:1024px)` to `@media (max-width:<mobile>px)`.

Confirm each old text occurs exactly once before you replace it. A `@media` line inside a `/* ... */` comment stays as it is. Send both fields in one `update`, then compare each field's read-back with your expected text. If off-canvas is limited to mobile through `offCanvasBreakpoint`, change it to match.

Never raise the breakpoint to get the menu button on desktop: set `enableOffCanvas` to `1`.

### Your own CSS

* Put it outside the Code Block, in a new Code Block placed below it in the header, or in the site's custom CSS, so a template update does not remove it. Ask the user which.
* The sidebar's CSS comes from the Code Block and uses `.breakdance` selectors with `!important` in places. Start every selector with `body`, for example `body .dwc-sidebar__nav__link`, and check it on the published page.
* Desktop-only rules start with `body:not(.dwc-mobile)`, mobile-only rules with `body.dwc-mobile`, collapsed-only rules with `body.dwc-collapse-sidebar`.
* Include the rules below the breakpoint in the same pass.
* Keep all your CSS in one local file in your working directory and save each element from it.

### Import, replace, files

* Never replace the header's tree, never delete the header, and never change its template conditions without the user asking.
* Do not use `breakdance-html-to-page` on the header. It only adds elements, and it would add a second sidebar.

***

## 6. Rules & gotchas

### Options

* `enableTopBar` needs `enableOffCanvas: 0`. `overlayTopBar` needs `enableOffCanvas: 1`. `overlaySidebar` needs `enableOffCanvas: 0`.
* `enableHeadroom` needs `enableOffCanvas` or `enableTopBar`, and stops working with `offCanvasPushContent`.
* The collapsible sidebar is desktop only and off whenever `enableOffCanvas` is `1`, at every width.
* `offCanvasBreakpoint` defaults to every width. Below `mq` there is always a mobile menu: don't turn on off-canvas to get one.
* `updateBackText` writes `back to <data-title>`. For other wording, set it to `0` and change the Back button's text element.
* `urlConfigMap` is read once at page load. `reinitialize()` doesn't apply it.
* `calcTopPadding` is read by the code but is not in the template's option list. With the top bar the template already pads the first section. For off-canvas on desktop, add `calcTopPadding: 1,` to the options.
* `calcHeaderHeight` is in the template's options but nothing reads it. Do not use it.

### Attributes

* `offcanvas` `"1"` with `enableOffCanvas: 0` breaks the layout: the nav hides off screen and the header stretches across the top. Logged-in users also see a red message.
* `enableOffCanvas: 1` with `offcanvas` `"0"` works, but the first frame can flash.
* `topbar` follows `enableTopBar` the same way.
* Attributes are on the header for every page. A page that turns on off-canvas through `urlConfigMap` keeps `offcanvas` `"0"`.
* `data-collapse` and `data-disable-motion-on-load` are removed by the sidebar's code 300 ms after load. A read of the published page shows them empty. That is normal.

### Panels and data-title

* A slide button opens the panel with the same `data-title`. Exact match, case and spaces included.
* Each panel's `data-title` is unique. With two the same, the button opens the first one.
* Use readable names: they are visible ("back to Services") and spoken ("Services menu").
* Every panel is a direct child of Nav.

### Code Block

* You edit the top of the one Code Block. Everything below `urlConfigMap` in the JS and below the `:root` rules in the CSS is product code.
* The JS runs inside a `DOMContentLoaded` function. `sidebar`, `DWCSidebarConfig` and `urlConfigMap` are not reachable from the page. `window.DWCSidebarNavigation` and `DWCSidebarNavigation.activeInstance` are.
* The Code Block's PHP field holds a leftover comment. Leave it.

### Element names

The template keeps its own spelling: `li -  dropdwon` (typo and double space), `mobile menu overaly`, `Sidebar  <header> v3.0.2`. Match by class first, then by label.

### Header

* The sidebar is `position: fixed` on desktop, at the start of the line. `enableRTL: 1` puts it on the right and turns the whole page right to left.
* Logged-in users have the WordPress admin bar. Offset anything you fix to the top with `var(--wp-admin--admin-bar--height, 0px)`.

***

## 7. Verification

A read-back proves configuration. Only the published page proves rendering. Say which you reached.

**A check that finds nothing is a failed check.** A selector that matches nothing returns `0` or `null`. Prove the element was found before you report on it.

**1. Fetch the published page** with a unique query string (`?nocache=<timestamp>`). The plain URL can be an old cached copy. The header renders for logged-out visitors on any page its conditions cover. Grep for what you changed: an attribute, a class, a link. Options and variables are not in the HTML: the Code Block's JS is, but its CSS comes from a generated stylesheet. Check those in the browser (step 2).

**2. Use your own headless browser** for position, size, computed style and behavior: `sidebar-test.mjs` in this folder. It needs Node 22+ and Chrome, and launches its own Chrome with a temporary profile. The import path is relative to your script.

```js
import { open } from '../sidebar-nav-breakdance-skills/sidebar-test.mjs';
const b = await open({ url: 'https://example.com/?nocache=' + Date.now(), width: 390, height: 844, mobile: true });
try {
  await b.sleep(2500);
  await b.tap('.dwc-nav-trigger'); await b.settle();
  console.log(await b.fn(() => document.body.className), await b.box('.dwc-sidebar__nav'), b.errors);
  await b.shot('menu.png');
} finally { await b.close(); }
```

* Never attach to the user's own Chrome or ask them to relaunch theirs with a debugging port.
* **The sidebar's code is running** when `<body>` has `show-nav`. Wait 2500 ms after load, then check. If it is missing, stop and tell the user (entry file, invariants).
* **Options:** `DWCSidebarNavigation.activeInstance.config.<option>` in the page is the live value.
* **Variables:** `getComputedStyle(document.documentElement).getPropertyValue('--name')`.
* Check desktop and a width below the breakpoint (`body` has `dwc-mobile`).
* Open the mobile or off-canvas menu with `tap('.dwc-nav-trigger')`, a slide panel with `click('.dwc-sidebar__nav__btn[data-title="<name>"]')`, collapse with `click('.dwc-toggle-collapse')`. Then `settle()` before measuring. After a collapse, wait 600 ms more for `dwc-is-collapsed`.
* Current-page behavior runs late: wait 2500 ms after load before you check which panel or dropdown opened.
* `saveCollapseState` keeps state in `localStorage` under `sidebarCollapsed`. Each `open()` starts with an empty profile.
* To test an option change before you save it: fetch the published page, change the option line in the page's inline script, serve the result from `127.0.0.1` with `<base href="https://the-site.com/">`, and open that. The page's own file does not need to be saved or deployed for this. Rebuild the copy before every run.
* When a rule of yours doesn't apply, run `why(selector, property)` before you change anything.
* In test URLs use `nocache` or long keys only. WordPress treats short keys such as `m`, `w`, `p` and `s` as its own and serves a different page.

**What you cannot check**, and must hand to the user: the builder view, drafts, and logged-in-only content.

***

## 8. Agent Skills Update routing (developer sessions)

| Discovery | Where it goes |
| --- | --- |
| New operation or tool pattern | Section 5: Operations |
| Mistake to avoid, tool behavior | Section 6: Rules & gotchas |
| Option, attribute, variable or class | Reference file, matching section |
| Verification technique | Section 7: Verification |

One line or a short code block. Confirmed only. State it as a present-tense rule: no dates, no story, no "an earlier version said".
