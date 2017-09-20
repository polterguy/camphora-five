
# Camphora Five - A CRUD app creator for Phosphorus Five

Camphora Five is a CRUD app generator for Phosphorus Five. It allows you to create simple CRUD apps, without
ever having done any previous coding at all. You simply declare which data columns your apps should have,
and the type of columns, for then to generate your app. The results becomes a nice CRUD app, with lots of
features, allowing you to Create, Read, Update and Delete data items from a MySQL database.

![alt screenshot](media/screenshots/screenshot-1.png)

Above is an example of an app with one _"textarea"_ column type, and one _"checkbox"_ column type.

Your apps will have support for importing and exporting items in CSV file format, and there will be a real
MySQL database which your apps use to store their data. In the above screenshot, you can see how the _"textarea"_
column type, has support for both Markdown, in addition to **#hash-tags** for its items. The latter allows
you to easily categorise your items as you see fit, using hash tags.

When you create your apps, there are many different settings you can choose from, to make sure your app becomes
just as you want it to be. For instance, you can choose if you'd like to show the headers for your data grid or not,
and which skin to use. Below is a screenshot of how Camphora looks like when you're creating your apps.

![alt screenshot](media/screenshots/screenshot-3.png)

Editing of items happens _"inline"_, by creating a form for your items content, which is injected into the page,
just beneath the item itself. Making editing of items a very pleasent experience.

![alt screenshot](media/screenshots/screenshot-2.png)

The apps you create using Camphora will be a _"real"_ Phosphorus Five application, and Camphora will create it as a separate
module, which you can distribute as you wish, using for instance [Hyperbuild](https://github.com/polterguy/hyperbuild). This allows
you to rapidly create a CRUD app, package it, and distribute it as you see fit, according to your needs.

## Features of a CRUD app

* Never ending scrolling to feed your grid with new items
* Import of CSV files at least partially matching your CRUD app's schema
* Export of your database items into CSV files, allowing you to edit and manipulate the items in e.g. Excel or Numbers
* Many different column types, including _"textarea"_, "text"_ (single line text), _"created date timestamp"_, _"number"_, etc.
* The _"textarea"_ column type support both Markdown and __#hash-tags__
* Searching to filter away items, both generically, and according to the value of some specific column
* Deleting all records at once
* Role based management of who are allowed to edit your data, and who are allowed to only see your data
* And of course, all 4 CRUD operations, such as Create items, Read items, Update items and Delete items



