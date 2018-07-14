## Column types

There are several different types of columns you can choose from when creating your fields. Below is a complete
list, and their most important traits explained.

* __Singleline text__ - A single line text type of field.
* __Multiline text__ - Multiple lines of text field.
* __Markdown content__ - A Markdown field, that you can edit using a web based Markdown editor, and that will be formatted as HTML or _"rich text"_ when displayed.
* __Checkbox__ - A yes/no type of field.
* __Number__ - A number type of input.
* __Date__ - A date type of input.
* __Datetime__ - A date and time type of input.
* __Select dropdown__ - Allows the user to select from a pre-defined set of different options from a _"dropdown"_ widget.
* __Radiobuttons__ - Similar to select dropdown, but will display the different options as radiobuttons.
* __Date/time created__ - Not per se an input field, but an automatically created field, that allows you to track when the item was actually created.
* __Created by__ - Also not an actual input field, but tracks what user created the record automatically.

The _"Date/time created"_ and _"Created by"_ field types, are not really input fields, and cannot be
changed - But rather serves to track at what exact date and time your item was created, and what user created
the item. Neither of these fields can be changed after the record has been created.

### Markdown content fields

These types of fields allows the user to apply rich formatting to text, using the Markdown syntax. The field
will be edited with a Markdown type of editor, and when displayed, it will be transformed into its rich text (HTML)
counterpart. This field does not allow for malicious HTML injection, since every time its value is displayed, by
default the value will be semantically checked for malicious HTML tags - Unless you create your own views, at which
point you'll have to explicitly _"white wash"_ your own HTML. The list of legal elements can be configured though,
and you can find it in your app's _"/configuration/"_ folder. Below is an example of the most important
formatting instructions you can use in a Markdown field.

```markdown
# Large header

## Smaller header

### Event smaller header (continues to 6)

_emphasized/italics text_

__bold text__

Some paragraph, declared by adding an additional carriage return after the above paragraph or element.
Notice, it overflows unto the next line, and can use _emphasize_ and __strong__ elements inline and
even [hyperlinks](https://github.com/polterguy/phosphorusfive) inline.

Another paragraph ...

[Some hyperlink](https://your-hyperlinks-url.com)

* A bunch of
* bulleted lists

1. A numbered
2. list
3. of items ...

> Quotation of some piece of text ...
```

The above will resemble the following when viewed ...

<div class="shaded rounded air-inner air bg">

# Large header

## Smaller header

### Event smaller header (continues to 6)

_emphasized/italics text_

__bold text__

Some paragraph, declared by adding an additional carriage return after the above paragraph or element.
Notice, it overflows unto the next line, and can use _emphasize_ and __strong__ elements inline and
even [hyperlinks](https://github.com/polterguy/phosphorusfive) inline.

Another paragraph ...

> Quotation of some piece of text ...

[Some hyperlink](https://your-hyperlinks-url.com)

* A bunch of
* bulleted lists

1. A numbered
2. list
3. of items ...

</div>

The entire specification for Markdown is beyond the purpose of this document. However, you can start
out [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) if you'd like to see
a more detailed description of all of its elements.

### Select and radiobutton fields

These items allows the user to select a value from a pre-defined list of options. When you create such items,
the field type definition will split in two, and expect you to supply a comma separated list of pre-defined
values, from which the end user can select from, as he is creating new items, or editing existing items.
An example of such a field could for instance be _"sex"_, containing a comma separated list of the following
values; _"male,female"_. When the user is creating or editing an item, he will have to choose from only _"female"_
or _"male"_ as his value for that specific field.

### Checkbox fields

A checkbox column type, simply allows the user to select _"yes/no"_ type of values, since either the checkbox
has been checked, or not.

### Date/time created fields

This field, will simply track when the item was created, and cannot be edited after the item has been created.
This can be useful to track the date and time of creation, and will be displayed as the exact date and time
of creation as you read your item later.

### Created by fields

This field automatically tracks what user created the record, and is in such a regard similar to the
Date/time created field in that it is not an _"input"_ field.
