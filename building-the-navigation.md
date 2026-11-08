---
icon: list-tree
---

# Building the Navigation

You build the menu inside the **Nav** element. Every panel sits directly inside **Nav**, and every menu item is an `li` inside a panel's **List &lt;ul&gt;**.

***

## Menu items

The template has three kinds of menu item. To add one, duplicate an item of the same kind and change it.

| Item | What it does |
| --- | --- |
| **li - link** | A plain link to a page. |
| **li -  slide button** | Opens a slide panel. The Home panel slides away and the new panel slides in. |
| **li -  dropdwon** | Opens a list of links below it, in place. |

{% hint style="info" %}
The last two names keep the spelling they have in the template, with the extra space and the typo in "dropdwon". Use them to find the items.
{% endhint %}

### Change a link

1. Select the link element inside the **li - link**. It is the element with the class `dwc-sidebar__nav__link`.
2. In its settings, set the link.
3. Select the text element inside it and change the text.
4. To change the icon, select the **link icon** element and pick another icon.

The sidebar marks the link to the page you're on, so visitors can see where they are. It matches the link's address with the page's address. Use the page's address or its slug, for example `sample-page`.

***

## Slide panels

A slide button opens the panel that has the same `data-title` attribute.

### Add a slide panel

1. Duplicate the **Slide Panel** element. Keep the copy directly inside **Nav**.
2. Select the copy, open **Advanced > Attributes** and set `data-title` to a new name, for example `Services`.
3. In the copy, change the heading in **Panel title wrap**, then build its list.
4. Duplicate an **li - slide button** where the new button should go, and change its text.
5. Select the **slide button** element inside it, open **Advanced > Attributes** and set `data-title` to the same name: `Services`.

Now the button opens the new panel.

### Naming panels

* **Each panel needs its own `data-title`.** If two panels share a name, the button always opens the first one.
* **The button and the panel must match exactly**, including capital letters and spaces.
* **Use a name people can read**, such as `Services`, not `slide2`. Visitors see it: the Back button reads "back to Services" when it goes back to that panel. Screen readers also hear it, as "Services menu".
* The **Home panel** is called `Home`. You can rename it, for example to `Main menu`. Back buttons then read "back to Main menu".

### Go deeper

To add another level, put an **li - slide button** inside a slide panel's list, and point it at another slide panel. Keep that panel directly inside **Nav** too, next to the others. A panel's level comes from the button that opens it, not from where the panel sits in the Structure panel.

### Back and Home buttons

Each slide panel has a **Panel header** with two buttons:

* **Back button** goes back one panel. With the `updateBackText` option on, it reads "back to" and the name of that panel. See [Sidebar Options](sidebar-options.md#navigation).
* **Home button** goes straight back to the Home panel.

***

## Dropdowns

### Nest a dropdown

1. Duplicate an **li -  dropdwon**.
2. Drag the copy into another dropdown's list: **li -  dropdwon > dropdown content > List &lt;ul&gt;**.

Each level can have its own indent, background and icon size. See [Styling](styling.md#dropdown-levels).

***

## Anything else in a panel

Panels are normal Breakdance elements, so you can put other elements in them. The template's slide panel has an image inside its first link, for example.

## Panel footer

The Home panel's **panel footer** holds the **Social wrapper** (the social icons) and a **Button**. Change them like any other Breakdance element. The Button has the `dwc-hide` class, so it hides when the sidebar is collapsed. See [Attributes & Classes](attributes-and-classes.md#helper-classes).
