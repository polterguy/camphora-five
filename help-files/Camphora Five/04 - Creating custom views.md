## Creating custom views

This is a fairly advanced concept, and requires you to understand Hyperlambda. However, it is also extremely
powerful, and literally allows you to take control over every single aspect of the rendering of your app - While
still getting to use your automatically generated Camphora Five _"backend"_. If your view
is named for instance `some-view`, and your app `address-book`, the URL to your view will become
`/address-book/some-view`.

From your view, you can take completely control over every aspect of your app, and really do whatever you
want to do. If you want to access your database from your view, you'll have to use code similar to
the following.

```hyperlambda
/*
 * First open up your main Camphora database connection.
 */
p5.mysql.connect:[camphora]

  /*
   * Then (for instance) select items from your address-book table.
   */
  p5.mysql.select:select * from address-book

    /*
     * Do something with the above results ...
     */
    for-each:x:/@p5.mysql.select/*

      // ... code to handle currently iterated item goes here ...
```

Of course, you could also choose to for instance insert items in your _"view"_. Or really do whatever you wish.
In fact, you don't even need to access your database at all from within your view. You could also create
a _"settings"_ view for instance, or a _"help"_ view, etc, etc, etc. Below is an example of a custom view
that was created wrapping a Camphora Five app.

https://phosphorusfive.files.wordpress.com/2017/12/screen-shot-2017-12-07-at-21-43-05.png

The above is an example of a CRUD app I created, based upon QR codes, that allowed guests to create _"micro blogs"_
about companies, and help market these companies on Facebook and other social media platforms. It was entirely
based upon Camphora Five, with a handful of custom views as addons. The above is one such custom view, that
allows the guest to read a _"micro blog"_. Below is an example of a _"create view"_ for the same app.

https://phosphorusfive.files.wordpress.com/2017/11/screen-shot-2017-11-21-at-08-03-00.png

If you combine Camphora Five with custom views, it can become a very powerful tool for you.


