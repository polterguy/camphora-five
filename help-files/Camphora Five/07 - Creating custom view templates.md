## Creating custom view templates

One really nice feature with Camphora Five is the ability to create _"custom views"_. Arguably the power
of this feature is only surpassed by your ability to create _"custom view templates"_. If you take some
time to invest in learning Hyperlambda, you can actually extend the view templates that your users can
use when creating their own views, by creating your own _"template view"_, and simply add it as a Hyperlambda
file to the _"/modules/camphora-five/helpers/view-templates/"_ folder. This allows you to extend the _"code
builder"_ features of Camphora Five.

This allows you to create your own _"wizards"_, where your users can by following a simple wizard, create
their own views, 100% visually, without needing to do any Hyperlambda programming themselves. To understand
how this process works, we'll have to dive into an example _"template view"_. Below is a minimalistic
example of such a _"template view"_.

```hyperlambda
/*
 * Contains the parts of this view that needs to be configured.
 */
.configure
  .description:@"Your description of your template view goes here ... (Markdown syntax allowed)"
  image:"https://your-server.com/some-image.png"
  text:Some variable

/*
 * Your views content goes here.
 * Notice how we can use '{Some variable}' in our code.
 */
micro.css.include
p5.web.page.set-title:{Some variable}
create-widget
  class:container
  widgets
    div
      class:row
      widgets
        div
          class:col-100
          widgets
            camphora.widgets.datagrid
              page-size:25
              edit:false
              delete:false
              headers:false

```

The above template view contains one _"variable"_, which is the `{Some variable}` parts of its code.
Since this variable is referenced in the __[.configure]__ parts as a __[text]__ input type, the wizard
will ask the user to provide its value when he goes through the process of asking the user how he
wants his view created. When the view is created, each occurency of `{Some variable}` in a node's
_value_ will be replaced dynamically with whatever value the user supplied as he followed the wizard.
The __[.configure]__ parts of your view again, is only used by the system as the user is following the
wizard. After the view has been created, the __[.configure]__ node will be entirely removed, before
the view is created.

You can also reference fields from your apps, by adding instead of a __[text]__ argument to your
__[.configure]__, instead add a __[field]__ argument. In addition you can restrict the field's type,
by adding arguments to you __[field]__ definition, where the name of this argument becomes the legal
type declaration for that particular field's type declaration.If you for instance instead of providing
a simple text input, want to reference a field, but restrict the field's type to being either a _"number"_,
or a _"text"_ field type, you can use the following code as an example.

```hyperlambda
/*
 * Contains the parts of this view that needs to be configured.
 */
.configure
  .description:@"Description"
  image:"https://your-server.com/some-image.png"
  field:Some field
    number
    text

/*
 * The rest of your template view's code goes here ...
 */
```

The __[image]__ and the __[.description]__ parts of your __[.configure]__ parts are simply an image
and a descriptive (Markdown) piece of text, explaining to the user what the view actually does. The
image is best served if it is 200px wide, but will be resized (down) if it is too big to adequately
display in the user's wizard.

### Conditional template views

Some views can only be successfully added to a Camphora app if the app conforms to some sort of
criteria. For instance, the _"count"_ template view can only be added to an app if the user has
declared one or more of these following fields

* __[select]__
* __[radio]__
* __[user]__
* __[checkbox]__

You can easily add up such conditions yourself, by providing a __[.condition]__ lambda to your
__[.configure]__ section, which is a piece of lambda, that will be evaluated for your view, and
if you return boolean _"false"_ from that lambda, the user will not be allowed to select that
particular _"template view"_ for his app. Below is an example of such a condition, that will
check to see if the app has either a __[select]__ or a __[radio]__ field, and if not, will not
allow the user to select that view, for that particular app.

```hyperlambda
/*
 * Contains the parts of this view that needs to be configured.
 */
.configure
  .description:@"Description"
  image:"https://your-server.com/some-image.png"
  .condition

    /*
     * Verifies that at least one field of type [select]
     * or [radio] exists for the app.
     */
    p5.web.widgets.find-first
      .fields
    micro.form.serialize:x:/-/*/*?value
    if:x:/@micro.form.serialize/*/field-type(/=select|/=radio)
      return:bool:true
    return:bool:false


/*
 * The rest of your template view's code goes here ...
 */
```

You can of course provide the above lambda as complex as you wish. However, don't make it too resource
expensive or time consuming, since this will create a lot of _"lag"_ as the user is trying to create
his views.

### Variable types

You can create the following _"static"_ variable types.

* __[text]__ - A static piece of text variable.
* __[radio]__ - A static radio button type of input choice.
* __[markdown]__ - A static piece of markdown input.

As we saw in our first example at the top of this document, in our `{Some variable}` example,
you can reference variables of the above types inside of your view's content, from your __[.configure]__
section, and such reference dynamic variable values that the user provides as he creates his view,
by following your wizard.

To see examples of how to create your own _"view templates"_, please refer to any of the existing
templates in the _"/modules/camphora-five/helpers/view-templates/"_ folder.

**Warning**, if you create your own view templates, you'll need to create a backup of these if you choose
to upgrade your Phosphorus Five installation - Since this process will overwrite this folder, deleting
your template views.

