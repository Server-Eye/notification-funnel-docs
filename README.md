# Notification Funnels
All notifications are funnelled through definied ```rules```. If a ```rule``` matches, the defined ```appliedObject``` overwrites the base message object.

## Rules

Each rule's conditions *must* have either an `all` or an `any` operator at its root, containing an array of conditions.  The `all` operator specifies that all conditions contained within must be truthy for the rule to be considered a `success`.  The `any` operator only requires one condition to be truthy for the rule to succeed.

```js
// all:
{
    "all": [
        { /* condition 1 */ },
        { /* condition 2 */ },
        { /* condition n */ },
    ]
}

// any:
{
    "any": [
        { /* condition 1 */ },
        { /* condition 2 */ },
        { /* condition n */ },
        {
            "all": [ /* more conditions */ ]
        }
    ]
}
```

Notice in the second example how `all` and `any` can be nested within one another to produce complex boolean expressions.

## Operators

Each rule condition must begin with a boolean operator(```all``` or ```any```) at its root.

The ```operator``` compares the value returned by the ```fact``` to what is stored in the ```value``` property.  If the result is truthy, the condition passes.

### String and Numeric operators:

  ```equal``` - _fact_ must equal _value_

  ```notEqual```  - _fact_ must not equal _value_

  _these operators use strict equality (===) and inequality (!==)_

### Numeric operators:

  ```lessThan``` - _fact_ must be less than _value_

  ```lessThanInclusive``` - _fact_ must be less than or equal to _value_

  ```greaterThan``` - _fact_ must be greater than _value_

  ```greaterThanInclusive```- _fact_ must be greater than or equal to _value_

### Array operators:

  ```in```  - _fact_ must be included in _value_ (an array)

  ```notIn```  - _fact_ must not be included in _value_ (an array)

  ```contains```  - _fact_ (an array) must include _value_

  ```doesNotContain```  - _fact_ (an array) must not include _value_

  ---

  The `notification funnel` feature and parts of this documentation are based on the [json-rules-engine](https://github.com/cachecontrol/json-rules-engine)
