# MakePlans Custom Forms - Version 1.0

## Get started

Booking, person, service, event, resource and category supports adding custom attributes via a customized form. The form is built with [Liquid](http://liquidmarkup.org). Please read the [Liquid documenation](https://github.com/Shopify/liquid/wiki) for more information. You can use HTML and all standard Liquid syntax. In additional to the standard Liquid tags MakePlans has made available various standard fields (for booking and person in public booking form) as well as custom field types (for booking, person, service, event, resource and category).

Fields will produce a `<label>` and `<input>` or other specified form field and wrapped in a container such as `<p>` or `<div>`.

Standard fields which fails validation will have the `<input>` field wrapped in a `<div class="field_with_errors">`.

There is no guaranteed way to validate custom fields. The only way to do some sort of validation is using JavaScript or HTML5 form validation which both can be skipped by the user.

## Data types

All values are stored as strings.

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

The html_options attribute is optional.

### Standard fields - public booking form

For all these fields you can ommit the label and it will use the standard label for the specified field. `{% name %}` will produce a label with 'Name'.

These fields are only applicable in the public booking form. They are already present in the administration forms.

Syntax: `{% field 'label', 'html_options' %}`

#### Name

Example: `{% name 'Your name' %}`

#### Email

Example: `{% email 'Your email' %}`

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

#### Text

Syntax: `{% text 'label', 'field_name', 'html_options' %}`.

Basic example: `{% text 'Describe yourself with one word', 'self_description' %}`

Extended example: `{% text 'Descibe yourself with one word', 'self_description', 'data-required="true"' %}`

#### Checkbox

Syntax: `{% checkbox 'label', 'field_name', 'html_options' %}`.

Example: `{% checkbox 'Do you want lunch?', 'lunch', 'checked="checked"' %}`

#### Select

Syntax: `{% select 'label', 'field_name', ['value1', 'value2'], 'html_options' %}`.

Example: `{% select 'Favorite colour', 'colour', [ 'Red','Yellow','Blue','Green' ], 'class="funkyclass"' %}`

#### Textarea

Syntax: `{% textarea 'label', 'field_name', 'html_options' %}`.

Example: `{% textarea 'Information from supplier', 'supplier_info' %}`

#### Hidden

Syntax: `{% hidden 'field_name', 'html_options' %}`.

Example: `{% hidden 'secret' %}`

#### Date

A date field will trigger a datepicker on the field in any form. In addition the name of the field should be suffixed with `_at` such as `last_visit_at`. This will ensure that the value is always treated as a date. Just using `date` will only ensure so visually in the form.

Syntax: `{% date 'label', 'field_name', 'html_options' %}`.

Example: `{% date 'Membership date', 'became_member_at' %}`