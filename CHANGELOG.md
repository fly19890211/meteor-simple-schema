simple-schema
=========================

A simple, reactive schema validation smart package for Meteor.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [simple-schema](#simple-schema)
  - [Change Log](#change-log)
    - [1.4.0](#140)
    - [1.3.3](#133)
    - [1.3.2](#132)
    - [1.3.1](#131)
    - [1.3.0](#130)
    - [1.2.0](#120)
    - [1.1.0](#110)
    - [1.0.3](#103)
    - [1.0.2](#102)
    - [1.0.1](#101)
    - [1.0.0](#100)
    - [0.7.0](#070)
    - [0.6.0](#060)
    - [0.5.1](#051)
    - [0.5.0](#050)
    - [0.4.0](#040)
    - [0.3.0](#030)
    - [0.2.48](#0248)
    - [0.2.47](#0247)
    - [0.2.46](#0246)
    - [0.2.45](#0245)
    - [0.2.44](#0244)
    - [0.2.43](#0243)
    - [0.2.42](#0242)
    - [0.2.41](#0241)
    - [0.2.40](#0240)
    - [0.2.39](#0239)
    - [0.2.38](#0238)
    - [0.2.37](#0237)
    - [0.2.36](#0236)
    - [0.2.35](#0235)
    - [0.2.34](#0234)
    - [0.2.33](#0233)
    - [0.2.32](#0232)
    - [0.2.31](#0231)
    - [0.2.30](#0230)
    - [0.2.29](#0229)
    - [0.2.28](#0228)
    - [0.2.27](#0227)
    - [0.2.26](#0226)
    - [0.2.25](#0225)
    - [0.2.24](#0224)
    - [0.2.23](#0223)
    - [0.2.22](#0222)
    - [0.2.21](#0221)
    - [0.2.20](#0220)
    - [0.2.19](#0219)
    - [0.2.18](#0218)
    - [0.2.17](#0217)
    - [0.2.16](#0216)
    - [0.2.15](#0215)
    - [0.2.14](#0214)
    - [0.2.13](#0213)
    - [0.2.12](#0212)
    - [0.2.11](#0211)
    - [0.2.10](#0210)
    - [0.2.9](#029)
    - [0.2.8](#028)
    - [0.2.7](#027)
    - [0.2.6](#026)
    - [0.2.5](#025)
    - [0.2.4](#024)
    - [0.2.3](#023)
    - [0.2.2](#022)
    - [0.2.1](#021)
    - [0.2.0](#020)
    - [0.1.13](#0113)
    - [0.1.12](#0112)
    - [0.1.11](#0111)
    - [0.1.10](#0110)
    - [0.1.9](#019)
    - [0.1.8](#018)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Change Log

NOTE: There was an accidental breaking change in v1.4.0. Probably only aldeed:collection2 is affected. If you use aldeed:simple-schema v1.4.0 or higher along with aldeed:collection2, be sure to use aldeed:collection2 v2.7.1 or higher.

### 1.5.3

Removed the old `SimpleSchema.prototype.validator`

### 1.5.2

The `ValidationError` thrown by `validate` now provides a useful error message so that it is clear what the first error is if it is not caught and is printed to console above the stack trace.

### 1.5.1

`mySimpleSchema.validate` now satisfies `audit-argument-checks`

### 1.5.0

- `mySimpleSchema.validate` now accepts the same second `options` argument that `validationContext.validate` does.
- `mySimpleSchema.validator` now takes an `options` argument. If you set the `clean` option to `true`, then the object will be cleaned before it is validated. If you want to change any of the default cleaning options, you can pass in those, too.

### 1.4.0

For compatibility with the new [mdg:method](https://github.com/meteor/method) package, two new functions have been added:

- Call `mySimpleSchema.validate(doc)` to validate `doc` against the schema and throw a `ValidationError` if invalid. This is like `check(doc, mySimpleSchema)` but without the `check` dependency and with the ability to pass full schema error details back to a callback on the client.
- Call `mySimpleSchema.validator()` to get a function that calls `mySimpleSchema.validate` for whatever object is passed to it. This means you can do `validate: mySimpleSchema.validator()` in the [mdg:method](https://github.com/meteor/method) package.

NOTE: There was an accidental breaking change in this release. Probably only aldeed:collection2 is affected. If you use aldeed:simple-schema v1.4.0 or higher along with aldeed:collection2, be sure to use aldeed:collection2 v2.7.1 or higher.

### 1.3.3

When using `check` to validate, the `Match.Error` that is thrown now explains which field failed to validate and why (only the first error). All errors can be found in an `invalidKeys` property on the `Match.Error` object.

### 1.3.2

Bug fixes and MongoDB 2.6+ compatibility fixes

### 1.3.1

* Fix "undefined is not allowed by the schema" error message
* Trim strings before removing empty strings so that `"   "` will be cleaned
* Don't type convert $unset values when cleaning

### 1.3.0

Added built-in regular expression `SimpleSchema.RegEx.ZipCode`

### 1.2.0

* The `clean` function now automatically converts a number or string to a Date object. (Thanks @rlora)
* Fix to `makeGeneric` handling when a property name starts with a number but also includes non-numeric characters. (Thanks @Nieziemski)
* New `exclusiveMax` and `exclusiveMin` options allow you to specify that the `min` or `max` value itself should not be considered valid. (Thanks @sleiber)

### 1.1.0

* Introduce the `pick` method on `SimpleSchema` instances to create subschemas
* Fixed `minDate` default validation error message
* Fix issue where `custom` functions were not run if the operator was $unset or $rename

### 1.0.3

Fix blackbox handling during filtering (thanks @wojtkowiak)

### 1.0.2

Fix label reactivity when calling `label` method with a key that contains a specific index piece (like ".0.")

### 1.0.1

Minor fix

### 1.0.0

* Internal support for specifying many of the schema options as functions. Still largely untested, so not yet documented.
* Removed some API functions from the `SimpleSchema` prototype: `requiredObjectKeys`, `requiredSchemaKeys`, `firstLevelSchemaKeys`, `customObjectKeys`. If you were using them, you should be able to use the new `objectKeys` function instead.
* When you filter an object by calling `mySimpleSchema.clean` with the `filter: true` option, it no longer filters out `$unset` keys that aren't defined in the schema. This is helpful in a case where you've changed the schema, removing a key, and now you want to run some conversion code to unset that key in documents where it already exists.
* Calling `mySimpleSchema.clean` now trims string values by default. To skip this, use the `trimStrings: false` option when you call `clean`. You can also set `trim: false` for any key in the schema definition to indicate that string values for that key must never be trimmed. This is useful for a property that stores a password or markdown or anything else where leading and trailing spaces may matter.
* Added `getErrorObject` function to `SimpleSchemaValidationContext` prototype. Mainly intended to be used by collection2 and autoform packages, but can be used anywhere you want to have an `Error` object that reflects the invalid schema context.
* Made `blackbox: true` work (and apply to all array item objects) when `type: [Object]`.
* Bump to 1.0.0 version to begin following semantic versioning standards more precisely.

### 0.7.0

BREAKING CHANGES!

* `SimpleSchema.RegEx.WeakEmail` has been removed, and `SimpleSchema.RegEx.Email` is now the regular expression recommended by W3C [here](http://www.w3.org/TR/html5/forms.html#valid-e-mail-address). This is a very permissive expression used by most browsers when `type=email`.
* Empty strings no longer cause a "required" error. If you don't want empty strings to be considered valid for a required key, be sure to clean your object before validating it.
* Fixed issue where `$set`ting an object property to an object that does not include all required properties was incorrectly considered to be valid.

### 0.6.0

BREAKING CHANGES!

* `regEx` messages must now be defined in a different way. Refer to the README.
* Removed support for `valueIsAllowed` option. Use `custom` instead.
* Remove `SchemaRegEx` exported variable. Use `SimpleSchema.RegEx` instead.
* Internal code reorg and cleanup
* When `removeEmptyStrings` option is enabled during cleaning, empty strings in `$set` are now translated to `$unset`.
* `$pull` operators that include a `query2` are now properly cleaned

### 0.5.1

Console logging about filtered and autoconverted fields now happens only when `SimpleSchema.debug = true`

### 0.5.0

* Additional built-in RegEx patterns, including an alternative e-mail pattern. See the readme. (Thanks @Nemo64)
* `SimpleSchema.clean` now removes empty string values by default. To prevent this, set the `removeEmptyStrings` option to `false`.

### 0.4.0

Add built-in regular expression `SimpleSchema.RegEx.Id` for id's generated by `Random.id()` of the random package, and also usable to validate a relation `_id`.

### 0.3.0

* Add `SimpleSchemaValidationContext.prototype.addInvalidKeys`. See "Manually Adding a Validation Error" in the README.
* Fix minor issues with filtering

### 0.2.48

Internal change: Add keepArrays option to mongoObject.getFlatObject, for use by autoform pkg.

### 0.2.47

Fix issue with setting autoValue for property of an object that's in an array, when cleaning a modifier.

### 0.2.46

Fix issue where blackbox objects were being validated in update modifiers. (Thanks @Pugio!)

### 0.2.45

Fix issue where some implied schema keys were not automatically added to complex schema definitions

### 0.2.44

* Ensure that custom validation functions are always called in even more situations,
but make sure that this doesn't cause unnecessary "required" errors.
* Add some `console.info` to help you see what is filtered out and autoconverted by the `clean` method.

### 0.2.43

Fix issue where default values were being added to update modifiers.

### 0.2.42

Ensure custom validation functions are always called, even when the field is undefined.

### 0.2.41

Added userId or `null` to custom validation and autoValue contexts when on the client.

### 0.2.40

Generate auto values after type conversion so that autoValue functions don't
have to handle type conversion. *(Thanks @mjgallag!)*

### 0.2.39

Fix issue with `autoValue` and `defaultValue` altering some updates.

### 0.2.38

* `autoValue` option moved from Collection2 package to SimpleSchema
* `defaultValue` option added
* Significant rewrite of `MongoObject` (used internally), which results in
fixing some obscure bugs and hopefully not creating any new ones.
* `clean` now does everything on the referenced object without cloning it. If
this is not what you want, then you should pass in a clone of the object you
want to protect and grab the resulting cleaned object from the return value.
* All types of custom validation functions now have the same `this` context.
* `siblingField()` method now available in `this` within both `autoValue` and
custom validation functions.
* `this.userId` is potentially available in custom validation functions. You
must pass it to `validate` or `validateOne` in the `extendedCustomContext` option.
Validation as part of Collection2 operations or AutoForm submissions provides
this automatically.

### 0.2.37

Fix a small issue with debug option.

### 0.2.36

You can now set `SimpleSchema.debug = true` to cause all named validation
contexts to automatically log all invalid key errors to the browser console.
This can be helpful while developing an app to figure out why certain
actions are failing validation.

### 0.2.35

* Fix an issue where properties could be removed during cleaning because they
start with the same string of characters as an invalid property.
* When determining which error message to display, we now look for the generic
key after the specific key. For example, the error message for "addresses.$.street"
will now be used for an error involving "addresses.0.street" when there is no
specific error message for "addresses.0.street".

### 0.2.34

`label` method now works correctly when passing in specific array keys, e.g.,
`array.0.name` as opposed to `array.$.name`

### 0.2.33

* Fix validation of `blackbox` objects
* Fix `labels` method
* Messages and labels are now reactive

### 0.2.32

* Add support for `blackbox` option. See README
* Ensure that NaN isn't considered a valid number

### 0.2.31

* When combining and extending SimpleSchema instances, the individual field
definitions are now extended, meaning that you can add or override the
schema options for an already-defined schema key.
* Error messages can now be defined globally using `SimpleSchema.messages()`.
Instance-specific messages are still supported and are given precedence over
global messages.
* The `label` option can now be a function that returns a string. Whenever you
need a schema key's label, use the new `mySchema.label(key)` method to get it.
* Support `custom` option. This will likely replace `valueIsAllowed` eventually.
Refer to "Custom Validation" and "Validating One Key Against Another" sections
in the README.

### 0.2.30

Made a change that fixes an issue with the autoform package. When you specified
a `doc` attribute for an autoform and that document was retrieved from a
collection that had helpers attached using the `collection-helpers` package,
the autoform fields were not populated with the values from the document. Now
they are.

### 0.2.29

* Autoconvert to numbers from strings using `Number()` instead of `parseFloat()`.
* Minor improvements to validation logic.
* README additions

### 0.2.28

Remove automatic call to `clean` when validating. This has no effect on
validation done through a collection with the `collection2` package. However,
validation done directly with a SimpleSchema instance will now catch more
schema issues than it previously did (since 0.2.18).

### 0.2.27

Clone schema argument before modifying it

### 0.2.26

Fix basic object checking for IE 8

### 0.2.25

Complete rewrite of the internal validation logic. This solves some sticky
issues with array validation in more complex objects. It should not affect
the API or validation results, but you may notice some additional or slightly
different validation errors. Also, if you make use of the internally cached
copy of the schema definitions (`ss._schema or ss.schema()`), you may notice
some differences there.

The main change internally is that an array definition is now split into two
definitions. For example, if your schema is:

```js
{
  myArray: {
    type: [String]
  }
}
```

It is internally split and stored as:

```js
{
  myArray: {
    type: Array
  },
  'myArray.$': {
    type: String
  }
}
```

### 0.2.24

* Correctly validate $inc operator
* Allow passing an array of schemas to SimpleSchema constructor, which merges
them to create the actual schema definition.

### 0.2.23

Fix an issue, introduced in 0.2.21, that prevented autoconversion of values
in arrays.

### 0.2.22

Add tests for MongoObject and fix some issues found by the tests.

### 0.2.21

Fix an issue where cleaning a doc would convert empty arrays to empty strings.

### 0.2.20

Improve and export `MongoObject` class for use by collection2 and others.

### 0.2.19

Make sure min/max string length settings are respected when there is also
a regEx option specified.

### 0.2.18

* Add support for named contexts. Use `mySimpleSchema.namedContext(name)`
method to access the named context, creating it if it does not exist yet.
* The `validate` and `validateOne` methods on a SimpleSchema context now
clean (filter and autoconvert) the doc before validating it. You should no
longer call the `clean` method yourself before validating. If you do have a
good reason to call the `clean` method before calling `validate` or
`validateOne`, then set the `filter` and `autoConvert` options to `false`
when calling `validate` or `validateOne` to prevent double cleaning.
* The `validate` and `validateOne` methods on a SimpleSchema context now return
`true` or `false` to indicate the validity of the document or field, respectively.
You do not need to call a separate method to check validity.

### 0.2.17

Throw an error when the modifier is an empty object for an update or upsert.
This prevents overwriting the entire document with nothing, leaving only
an `_id` field left.

### 0.2.16

Fix handling of min or max when set to 0.

### 0.2.15

Adjust handling of validation errors for arrays of objects. Now when a validation
error is added to the list for a property of an object that is a member of an
array, the key name is listed with the array index instead of a dollar sign. For
example, `friends.0.name` instead of `friends.$.name`.

### 0.2.14

* Ensure valueIsAllowed function is called for undefined and null values. This
change means that you must not ensure that your valueIsAllowed function returns
true when the value is `null` or `undefined`, if you want the field to be optional.
* Fix an issue with false "required" errors for some arrays of objects when
validating a modifier.

### 0.2.13

Fix $pullAll and clean $pushAll by converting it to $push+$each rather than
deleting it.

### 0.2.12

Add workaround for Safari bug.

### 0.2.11

`Clean` method should now clean everything.

### 0.2.10

Validate upserts

### 0.2.9

Fix validation of required subobjects when omitted from a $set

### 0.2.8

* Add label inflection and allow labels to be changed dynamically with `labels` method.
* Allow min and max to be a function that returns a min/max value
* Allow array of regEx with specific messages for each

### 0.2.7

Refactor validation loop to improve and not use collapse/expand

### 0.2.6

Add subschema support (@sbking) and use Match.Any for `type` schema key test

### 0.2.5

Fix validation of $push or $addToSet for non-objects

### 0.2.4

Fix validation of objects as values of modifier keys

### 0.2.3

Fix validation of custom objects

### 0.2.2

Fix validation of arrays of objects

### 0.2.1

Fix minor issues related to $unset key validation

### 0.2.0

*(Backwards compatibility break!)*

* Validation contexts are now supported, allowing you to track validity separately for multiple objects that use the same SimpleSchema
* Some of the API has changed, related to the support for validation contexts
* All mongo modifier operators are now recognized and properly validated; as part of this, you must now tell the validation functions whether you are passing them a normal object or a mongo modifier object
* Validation errors are now thrown if fields not allowed by the schema are present in the object
* When you create a schema, your definition object is now checked to make sure you didn't misspell any of the rules

### 0.1.13

* A SimpleSchema object is now a valid second parameter for the built-in `check` and `Match.test` functions
* `.match()` method is deprecated

### 0.1.12

Return true from `match()`

### 0.1.11

Fix issue where `filter()` could strip out `$` keys

### 0.1.10

Support custom validation functions (used by collection2 package)

### 0.1.9

Pass doc to `valueIsAllowed` function so that validating one key against another is possible

### 0.1.8

Deprecated the regExMessage key in schema definition and replaced with the
ability to customize all validation error messages per error type and per schema
key if necessary. Refer to the Read Me.
