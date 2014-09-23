# MakePlans Custom Forms - Version 1.0

## Get started

Booking, person, service, event and resource supports adding custom attributes via a customized form. The form is built with [Liquid](http://liquidmarkup.org). Please read the [Liquid documenation](https://github.com/Shopify/liquid/wiki) for more information. You can use HTML and all standard Liquid syntax. In additional to the standard Liquid tags MakePlans has made available various fields (booking and person) as well as custom field types (all objects).

Fields will produce a `<label>` and `<input>` or equivialnt field, as well as a wrapper such as `<p>` or `<div>`.

Fields with error will have the `<input>` field wrapped in a `<div class="field_with_errors">`

## Complete example

### Public booking form

```
{% name %}
{% phone 'Mobile phone number' %}
{% checkbox 'Do you want lunch when you arrive?', 'lunch', 'checked="checked"' %}
```

### Service administration form

```
{% textarea 'Information from supplier', 'supplier_info' %}
{% select 'Expertise level', 'level', [ 'Beginner','Average','Expert' ] %}
```

## Fields

### Standard fields - public booking form

For all these fields you can ommit the label and it will use the standard label for the specified field. `{% name %}` will produce a label with 'Name'.

These fields are only applicable in the public booking form. They are already present in the administration forms.

Syntax: `{% field 'label' %}`

#### Email

Example: `{% name 'Your name' %}`

#### Phone

Example: `{% phone 'Telephone number' %}`

#### Note

Example: `{% note 'Additional details' %}`

#### Date of Birth

Example: `{% date_of_birth 'Your birthday' %}`

#### National Id Number

Example: `{% national_id_no 'Social Security Number' %}`

#### Street

Example: `{% street 'Street' %}`

#### Postal code

Example: `{% postal_code 'Zipcode' %}`

#### City

Example: `{% city 'Town' %}`

#### State

Example: `{% state 'State' %}`

#### Country

Example: `{% country_code 'Country' %}`

### Custom fields - all forms

Custom fields can be used in both the public booking form and all administration forms.

The html_options attribute is optional.

#### Text

Syntax: `{% text 'label', 'field_name', 'html_options' %}`.

Example: `{% text 'Descibe yourself with one word', 'self_description', 'data-required="true"' %}`

#### Checkbox

Syntax: `{% checkbox 'label', 'field_name', 'html_options' %}`.

Example: `{% checkbox 'Do you want lunch?', 'lunch', 'checked="checked"' %}`

#### Select

Syntax: `{% select 'label', 'field_name', ['value1', 'value2'], html_options' %}`.

Example: `{% select 'Favorite colour', 'colour', [ 'Red','Yellow','Blue','Green' ], 'class="funkyclass"' %}`

#### Textarea

Syntax: `{% textarea 'label', 'field_name', 'html_options' %}`.

Example: `{% textarea 'Information from supplier', 'supplier_info' %}`

#### Hidden

Syntax: `{% hidden 'field_name', 'html_options' %}`.

Example: `{% hidden 'secret' %}`