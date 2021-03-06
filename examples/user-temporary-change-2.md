# User temporary change - 2

Change a notification to a different user.

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
            "userId": "c3a796b7-2ea4-4b3b-b327-6a72279060a2",
            "prename": "Roland",
            "surname": "Paltz",
            "email": "roland.paltz@server-eye.de",
            "phone": ""
        }
    }
}
```