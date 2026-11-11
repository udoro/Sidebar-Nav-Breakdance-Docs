---
icon: sparkles
---

# AI Skills Reference

Entry point for configuring Sidebar Navigation Builder for **Breakdance** through the Breakdance MCP tools.

**This file is short on purpose. Read all of it, then read only what it sends you to.**

| File | What it is | When to read it |
| --- | --- | --- |
| `sidebar-nav-breakdance-skills-build.md` | Workflow, tool calls, rules and gotchas, verification | In full, on the build path only |
| `sidebar-nav-breakdance-skills-reference.md` | Element map, JS options, attributes, CSS variables, classes | Never in full. Grep one section |
| `sidebar-test.mjs` | Headless Chrome helper: open the page, act, measure, screenshot | Import it when the build file's Verification needs a browser. Don't read it unless it fails |

***

## Is the site connected

The Breakdance tools are named `breakdance-<action>` (for example `breakdance-get-post-tree`). Your client may prefix them with the server name. If your client defers MCP tools, load them by name first.

* **No `breakdance-*` tools:** stop. Tell the user: "I can't reach your Breakdance site. Follow the AI Connector setup, then start a new session." Do not try REST calls, PHP or a browser instead.
* **Before your first read or write in a session,** call `breakdance-get-instructions`. The server requires it before any build or edit tool. Its output is long and is saved to a file. You don't need Breakdance's `building-sites` or other skills for this product's menu items, options or variables: these files replace them.
* **A tool refuses a call:** name the error to the user, give them the builder steps for that change, and carry on with the rest. Never route around a refusal.

If your client also has Breakdance's own skills (`breakdance-get-skill`), load the matching one for generic Breakdance work such as templates or dynamic data. This file covers what is specific to Sidebar Navigation Builder.

***

## Which path are you on

**Correction path:** you are changing things that already exist, one or many: JS options, CSS variables, attributes, a menu item's text, link or icon. For more than one value, also read build file section 4. If a value can't do it, read "Your own CSS" in section 5. Verify as section 7 says.

**Build path:** you are creating structure: new menu items, panels or dropdowns, or a rebuild.

If you cannot tell, you are on the build path. If a correction turns out to need new structure, stop and switch at that point.

***

## Correction path

Read these three things and nothing else:

1. **The invariants below.**
2. **Section 6 (Rules & gotchas) in `sidebar-nav-breakdance-skills-build.md`**, grepped for the feature you are touching, and the Operations entry for the write you will make (section 5).
3. **One row** of the reference file, for the option, attribute or variable you are changing.

Then find the header (below), change the one value, verify, stop.

**Do not** read the build file end to end, read the engine part of the code field, re-read the whole tree after every write, or inventory anything you are not touching.

### Invariants that apply on every path

* **You edit one element: the Code Block labelled `Sidebar Nav Codes`** (the element whose `javascript_code` contains `const DWCSidebarConfig`). Options are at the top of its `javascript_code`, variables are at the top of its `css_code`. Everything below `urlConfigMap` in the JS, and everything below the `:root` blocks in the CSS, is product code: never change it, except the documented breakpoint change. To change behaviour beyond options and variables, add your own CSS outside the Code Block.
* **Change one value with a targeted replace.** Replace the exact text of that one line, with its indent and line break, confirm it occurs once, and write the whole field back. The commented `urlConfigMap` example repeats option lines such as `enableCollapsibleSidebar: 0,`. Never rewrite or reformat the rest of the field.
* **Write a code field so it arrives exactly.** Build the new field with `node` from the field you saved: replace the lines, then `JSON.stringify` it for the call. Make every change to one field in one write. Compare the read-back with your file byte for byte. If you can't send the field exactly, set the variable in your own Code Block instead (`body #dwc_header { --name: value; }`, see "Your own CSS" in the build file) and say so.
* **Options are `1` or `0`**, except `reinitOnUrlChange` (`true`/`false`) and the breakpoints (`window.matchMedia("(max-width: Npx)")`).
* **`offcanvas` and `topbar` are attributes on the root section and follow their options.** `enableOffCanvas: 1` needs `offcanvas` `"1"`. `enableTopBar: 1` needs `topbar` `"1"`. Set both together in one pass. Back to `0`, the same.
* **Attribute lists are written whole.** Send the full `settings.advanced.attributes` list with every row, changing only the `value` you mean to.
* **Element IDs are site-local.** Resolve them from the live tree every session. Never use an ID from any document, including this one.
* **A slide button opens the panel with the same `data-title`.** Exact match, unique per panel, readable: visitors see "back to <data-title>".
* **A success response proves the value was saved, not that it rendered.** Check the published page before you call a change done, and say which level you reached.
* **If the sidebar's code stops running** (`<body>` never gets `show-nav`), stop and tell the user. Do not retry the write.
* **A refused write:** name the error to the user, give them the builder steps, and carry on with the rest.

### Find the header

1. `breakdance-search-posts` with `post_type` `breakdance_header`. More than one: continue with all of them.
2. Read each candidate's tree with `breakdance-get-post-tree` and save it to a file. The Sidebar Navigation Builder header has a root `Section` with id `dwc_header` and the classes `dwc-sidebar` and `dwc-offcanvas-header`, and a Code Block whose `javascript_code` contains `const DWCSidebarConfig`. Identify the Code Block by that text, not by its position: a header can have more Code Blocks.
3. More than one match: ask the user which, by template title. None: see the build file, section 2.

Record the post ID and the IDs of the root section, the Code Block, the header inner wrap, Nav and the Home panel.

Compare the live option names with reference section 3. The post title and the root label are not proof of the version. Where the live code and the reference differ, the live code is authoritative.

### When the page disagrees with the builder

**Always fetch a published page with a unique query string** (`?nocache=<timestamp>`). Hosts and CDNs serve old copies of the plain URL. A response header reporting a cache hit (`x-hcdn-cache-status`, `cf-cache-status`, `x-cache`, `x-litespeed-cache`) means the copy may predate your change: fetch again with a new query string.

Cheapest cause first, stop at the first hit: **did the write land on the header you checked** (the tool response names the post ID), **was the copy cached** (above), **do the header's template conditions cover this page**. Three checks is the budget. If none explains it, report the discrepancy and stop. Never sweep other pages or audit the site.

***

## Build path

Read `sidebar-nav-breakdance-skills-build.md` in full, then follow its workflow from "START HERE". Everything above still applies.

***

## Agent Skills Update

Where you record a finding depends on the session. Decide before writing anything. A session is a **developer** session when `BREAKDANCE/SIDEBAR NAV BREAKDANCE/sidebar-nav-dev-context.md` is found by searching upward from this file's folder, and a **user** session otherwise.

| Session | Record findings in | Never edit |
| --- | --- | --- |
| **Developer** | these skills files, routed by the table in the build file | `sidebar-nav-breakdance-user-context.md` |
| **User** | `sidebar-nav-breakdance-user-context.md`, in this folder | these skills files |

**If you cannot tell, treat it as a user session.** On a user install these files are overwritten by the next update.

**Ask before you write, in either session.** Show the exact text, name the file and section, and wait for agreement. If the answer is no, drop it rather than recording it somewhere else.

***

## Before you say you are done

End every task with a short report. Five lines, not a paragraph.

**Time.** Always give it. Run `date +%s` when you start and again at the end. If the task spans several messages, save the start value in a file, so a context summary can't lose it.

**Calls.** How many Breakdance tool calls you made.

**What changed.** Elements, attributes, variables and options you touched, by name. Name headers and elements by their title, not only their ID. If you replaced or deleted anything, say so first.

**Custom code.** Name every place that now holds CSS or JS that the template doesn't ship: each element, Code Block or stylesheet, and what it styles. Say where the mobile rules are. Write `Custom code: none` when you added none, and `No custom JS` when it is all CSS.

**What you verified, and how.** Say which level you reached: saved (read-back) or rendered (published page). Name anything you could not check as unverified.

**Do not report tokens or cost.** You cannot measure them.

```
3m 40s, 5 Breakdance calls.
Changed: Sidebar Nav Codes enableCollapsibleSidebar 0 -> 1, hoverToExpandSidebar 0 -> 1; --sidebar-link-color dimgray -> #1a1a2e.
Custom code: none.
Verified: rendered. Published page at 1440px: DWCSidebarNavigation.activeInstance.config.enableCollapsibleSidebar is 1, collapsed width 68px, tooltips on 13 items.
Unverified: builder view.
```
