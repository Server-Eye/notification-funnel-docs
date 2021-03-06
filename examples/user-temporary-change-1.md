# User temporary change - 1

Change a notification to a different mail adress.

This sample expects that you have configured notifications for a user.

## Rule
```js
{
	"all": [
		{
			"fact": "context",
            "path": "$.user.email"
			"operator": "equal",
			"value": "kim.schneider@server-eye.de"
		},{
            "fact": "date",
            "operator": "greaterThanInclusive",
            "value": "2021-03-01"
        },{
            "fact": "date",
            "operator": "lessThanInclusive",
            "value": "2021-03-08"
        }
	]
}
```

## Fix
```js
{
    "context": {
        "user": {
            "email": "kim.schneider@anotherdomain.com"
        }
    }
}
```