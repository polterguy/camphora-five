## Manually editing your app

When you have generated your app, you can use Hyper IDE to edit your app's files. If your app's name is
for instance _"address-book"_, then you can find your app's files in the folder _"/modules/address-book/"_.

**Warning** - If you edit your app, for then to later re-generate your app, your changes will be lost, since
the generating process overwrites all files from your app's folder.

Your app's structure is the same as any other module you have in your Phosphorus Five installation. The
actual process of editing your app though, is beyond the scope of this documentation, and requires you to
understand Hyperlambda. However, for your convenience, I have included a snippet of Hyperlambda below, that
allows you to see all the possible icons you can use for your app. If you want to change your app's icon,
you can evaluate the snippet below, for then to edit your app's _"desktop.hl"_ file, and change the parts
of your `class` property that declares which icon to use.

```hyperlambda-snippet
/*
 * Loading HTML example file for IcoMoon.
 */
load-file:"/modules/micro/media/fonts-demo.html"

/*
 * Semantically iterating each "icon-x" class from HTML document retrieved above,
 * and adding one "li" element for each into our [create-widgets] invocation below.
 */
html2lambda:x:/@load-file/*?value
for-each:x:@"/@html2lambda/**/\@class/""=:regex:/icon-.{1,}/""?value"
  eval-x:x:/+/*/*/*/*/*
  add:x:/../*/create-widgets/**/ol/*/widgets
    src
      container
        element:li
        style:"font-size: 2rem;"
        widgets
          span
            innerValue:
            class:x:/@_dp?value
          span
            innerValue:" - "
          span
            innerValue:x:/@_dp?value

/*
 * Creating a widget wrapping each icon from IcoMoon.
 */
create-widgets
  micro.widgets.modal:dox-icons-modal
    widgets
      div
        class:air
        widgets
          h3
            innerValue:Available icons
          ol
            widgets
```

Below is an example of a _"desktop.hl"_ file from a Camphora Five generated app. If you change the `icon-paragraph-justify`
parts of your **[class]** declaration to any of the values that you found by evaluating the above Hyperlambda snippet,
your app's desktop icon will change accordingly.

```hyperlambda

/*
 * This is a _"template file"_, implying this file will be copied into
 * your Camphora Five generated app's folder when your app is generated,
 * and possibly modified to reflect your app's name/structure.
 *
 * Desktop widget file for Camphora generated apps.
 */
container
  element:a
  class:jumbo-button
  widgets
    literal
      element:span
      innerValue:address-book
      class:capitalize
    literal
      element:span
      class:icon-paragraph-justify
```

### Camphora Five's internals

To understand how to manually edit your app, it might help to understand some of the internals behind Camphora Five.
Inside Camphora Five's main modules folder, which you can find in _"/modules/camphora-five/"_, using for instance
Hyper IDE - There is a folder called _"/template/"_. This folder will be used as a template folder to create a plain
and normal Phosphorus Five module. The template folder again will contain most of the default files necessary to wire
up your Phosphorus Five application, such as a _"desktop.hl"_ file, a _"launch.hl"_ file, etc.

When your app is generated, it works in most regards exactly as any other type of Phosphorus Five module, and
if you know Hyperlambda, and the Micro extension widgets, you can easily edit your app, and modify it
as you see fit.

One detail though, is that each _"view"_ you create, can be found within the _"/views/"_ folder. This folder by
default will only contain one view, called _"default.hl"_. This is per se your main view for your app, and is quite
easily edited in fact. This default view instantiates two custom extension widgets that were automatically created
as your app was generated. These widgets are as follows.

- __[camphora.widgets.xxx.toolbar]__ - The toolbar for your app, with the pager, filter textbox, etc.
- __[camphora.widgets.xxx.datagrid]__ - The actual datagrid for your app.

Notice, the _"xxx"_ parts above are of course the name of your app. As you instantiate your toolbar and datagrid,
you can apply some arguments, to for instance prevent editing, setting the page-size, etc. These extension widgets
can also (obviously) also be consumed in your own views.

#### About Markdown and Multiline fields

When Markdown for multiline text elements is created, Camphora Five will load your _"html-whitelist.hl"_ file, for your
app, inside of your app's _"/configuration/"_ folder. This allows you to modify the legal HTML elements for your
particular app. Markdown is created as a _"leaky format"_, which allows you to create HTML tags inside
your Markdown. These tags will be rendered _"as is"_ in your resulting HTML. However, your HTML
whitelist file, declares which HTML elements and attributes of HTML elements are legal to render here - But only for your
specific app, and not all apps in general. Any HTML tag found in a Markdown field, that does not exist in
your whitelist file, will simply be entirely removed, preventing injection of malicious HTML tags into
your dataset.

**Notice**, if you create your own custom views, rendering Markdown, you need to make sure yourself that
no malicious HTML tags are injected into your resulting HTML!
