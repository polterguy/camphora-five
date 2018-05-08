## Creating custom views

Creating custom views have been significantly simplified in Camphora Five lately, and you
can now create fairly advanced _"views"_, without any coding experience at all. What views you
can add to your application, depends upon what fields you have in your app - However, you can
also create your own custom view entirely from scratch if you know some Hyperlambda. The latter
allows you to completely override the entire rendering of your page, and literally create _anything_
as a _"view"_ in your app. However, the simplest way to create a view, unless you want to teach
yourself Hyperlambda - Is to simply follow the _"wizard"_, and let Camphora Five automatically
create your code. Below is a screenshot of this process.

https://phosphorusfive.files.wordpress.com/2018/05/camphora-five-screenshot-create-view-pie-chart.png

Each view has its own unique settings. Often these settings are associated with fields in your app,
such as the above view that allows you to count the number of items grouped by the value of
one of your fields. If you for instance had one _"Created by"_ field in your app, you could use the
_"count"_ view to count each item created by your employees, where each employee has his own username
to your app, and is allowed to somehow create records in your Camphora app. Then you could choose
to view the number of items created by your employees, either as a _"pie chart"_ (see screenshot),
or as a _"bar chart"_, to such create statistical data of how your employees are performing.

In fact, the _"sales"_ example app in Camphora Five illustrates a couple of different statistical
charts. You can of course use this app as a template for your own apps, and modify it according to
your needs.

If you want to completely create your own view from scratch, you can easily do this by first creating
your app, and the open up your apps _"/views/"_ folder in for instance Hyper IDE, and create your
own Hyperlambda files in here. Your views will automatically populate the _"Views"_ toolbar, which
for the record is hierarchical, allowing you to even group your different views into folders and
sub-folders, and create entire hierarchies of such _"views"_.

**Warning** - If you start editing your app's folder's content after you have generated it, you
will _loose all of your edits_ if you for some reasons re-generate your app!
