---
title: difference() function
description: placeholder
menu:
  flux_0_7:
    name: difference
    parent: Functions
    weight: 1
---

The `difference()` function computes the difference between subsequent non-null records.

_**Function type:** aggregate_  
_**Output data type:** float_

```js
difference(nonNegative: false, columns: ["_value"])
```

## Parameters

### nonNegative
Indicates if the difference is allowed to be negative.
When set to `true`, if a value is less than the previous value, it is assumed the previous value should have been a zero.

_**Data type:** boolean_

### columns
A list of columns on which to compute the difference.
Defaults to `["_value"]`

_**Data type:** array of strings_

## Examples
```js
from(bucket: "telegraf/autogen")
  |> range(start: -5m)
  |> difference()
```
```js
from(bucket: "telegraf/autogen")
  |> range(start: -5m)
  |> difference(nonNegative: true)
```