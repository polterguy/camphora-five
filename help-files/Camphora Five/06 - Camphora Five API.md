
## Camphora Five API

Camphora Five has a rich API. In addition, it also creates an API for your apps. The most important
parts of your app's API are the following extension widgets.

- __[camphora.widgets.xxx.toolbar]__ - The toolbar for your app, with the pager, filter textbox, etc.
- __[camphora.widgets.xxx.datagrid]__ - The actual datagrid for your app.

These extension widgets allows you to override arguments to your app, as you instantiate them.
For instance, you can set an initial _"search query"_, the initial page, whether or not editing of items
is allowed, etc.

**Notice**, the `xxx` parts from these active events is of course the name of your app. Implying if your
app's name is `address-book`, the name of its datagrid extension widget becomes
__[camphora.widgets.address-book.datagrid]__. You can use these extension widgets in your own views,
or other modules, as you see fit. However, you can only instantiate _one_ of these widgets in each page.
Or to be explicit, you can instantiate one of _each kind_ in each page.

**Also notice**, your datagrid extension widget _must_ be given the ID of `camphora-datagrid`.

### Widget lambda events

The above datagrid widget has the following widget lambda events.

- __[camphora.create-new-item]__ - Displays a modal widget allowing the user to supply values for a new data item.
- __[camphora.download-items]__ - Downloads entire dataset to client as a CSV file.
- __[camphora.datagrid.sort]__ - Sorts the datagrid. Supply __[column]__ as whatever column/field you want to sort your datagrid according to.
- __[camphora.datagrid.search]__ - Filters your datagrid according to the given __[\_arg]__ argument.
- __[camphora.datagrid.page.previous]__ - Pages your datagrid to its previous page, if possible.
- __[camphora.datagrid.page.next]__ - Pages your datagrid to its next page, if possible.
- __[camphora.datagrid.databind]__ - A much more _"low level"_ way to databind your datagrid, allowing you to supply a __[filter]__ argument directly, instead of a _"search query"_ argumen.
- __[camphora.database.import-csv-file]__ - Imports the given __[\_arg]__ CSV file into your database.
- __[camphora.database.delete-all-items]__ - Will display a modal widget asking for user's confirmation, and if confirmation is given, it will delete every single item from your database.
- __[camphora.database.update]__ - Updates an existing item. Pass in __[id]__ as your item's database id, and any other fields you want to update as a key/value collection.
- __[camphora.database.insert]__ - Inserts a new item into your database.

In addition to the above Active Events, the datagrid of your Camphora Five app will also _"publish"_ a couple of
Active Events when some sort of event occurs. Below is a list of these events.

- __[camphora.filter-changed]__ - Invoked when your datagrid's filter is for some reasons changed.
- __[camphora.datagrid.databound]__ - Invoked when for some reasons the datagrid is databound.
- __[camphora.count-changed]__ - Invoked when for some reasons the count of items in your database has changed.
- __[camphora.sort-changed]__ - Invoked when for some reasons the sorting of your datagrid has changed.

By consuming the above Active Events and extension widgets yourself, you can take completely control over
how your apps are wired together, and for instance create your own paging logic, filtering logic, and completely
for instance drop the default toolbar, etc. Assuming you have created an app called `address-book`, you
can evaluate the snippet below to see an example of consuming the API directly yourself, to display only
the first 5 items, not allowing for editing items at all.

```hyperlambda-snippet
/*
 * Creates a modal widget displaying the address-book
 * app, without any toolbars, displaying the 25 first items.
 */

/*
 * Making sure we include app's CSS file.
 */
p5.web.include-css-file:/modules/address-book/media/main.css

/*
 * Creating our actual modal widget.
 */
create-widgets
  micro.widgets.modal
    widgets
      camphora.widgets.address-book.datagrid:camphora-datagrid
        page-size:5
```
