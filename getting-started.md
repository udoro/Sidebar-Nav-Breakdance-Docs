---
icon: desktop-arrow-down
---

# Installation & Getting Started

## Before you start

You need **Breakdance** on a WordPress site, and an account that can open the builder.

***

## Installation

Do all three steps, in order.

### 1. Create a header template

1. In WordPress, go to **Breakdance > Templates**.
2. Create a new header template, for example `My Sidebar Header`.
3. Show it on **Everywhere** to put the sidebar on every page. Or pick only the pages it should show on.
4. Open the template with the Breakdance builder.

### 2. Paste the sidebar

1. Download the JSON file from your Gumroad library.
2. Open the file in your browser, or in any text editor.
3. Select all the text and copy it.
4. In the builder, click the canvas of your empty header and paste (Ctrl+V on Windows, Cmd+V on Mac).
5. Save.

The sidebar now shows in the builder.

### 3. Check it on your site

Open one of the pages the header applies to. The sidebar shows on the left on desktop. On a small screen it turns into a menu button that opens the sidebar.

***

## Put the sidebar on the right

Set the `enableRTL` option to `1`. See [Sidebar Options](sidebar-options.md#right-to-left).

`enableRTL` turns the whole page right to left, not only the sidebar. Text direction changes too. Use it when the sidebar belongs on the right.

***

## What's inside the template

```
Sidebar <header>            (section: the sidebar attributes)
├── header inner wrap       (top of the sidebar, or the top bar)
│   ├── Logo wrapper        (your logo, as a link)
│   ├── trigger wrapper
│   │   └── mobile menu trigger   (opens the mobile and off-canvas menu)
│   └── Collapse toggle     (collapses the sidebar)
├── Nav                     (holds every panel)
│   ├── close btn           (closes the mobile and off-canvas menu)
│   ├── Home panel          (the first panel, always there)
│   │   ├── inner wrap
│   │   │   └── List <ul>
│   │   │       ├── li - link            (a plain link)
│   │   │       ├── li - slide button    (opens a slide panel)
│   │   │       └── li - dropdown        (opens a list in place)
│   │   └── panel footer    (social icons and a button)
│   └── Slide Panel         (opened by a slide button)
│       ├── Panel header    (Home button and Back button)
│       └── inner wrap
│           ├── Panel title wrap
│           └── List <ul>
├── mobile menu overaly     (the dark layer behind the open menu)
└── Sidebar Nav Codes       (Code Block: your options, your CSS variables, and the sidebar's code)
```

* You build your menu inside **Nav**. See [Building the Navigation](building-the-navigation.md).
* You edit the top of the **Sidebar Nav Codes** Code Block. See [Sidebar Options](sidebar-options.md) and [Styling](styling.md).
* The **Sidebar &lt;header&gt;** section holds a few attributes. See [Attributes & Classes](attributes-and-classes.md).

{% hint style="info" %}
The **mobile menu overaly** element keeps the spelling it has in the template. Use that name when you look for it.
{% endhint %}
