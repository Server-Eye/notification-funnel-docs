# SLA : disable notification

Disable notifications based on utc time, day of week and if the customer has a specific ```SLA``` property.

This sample expects that you have configured notifications with enabled email, sms, etc.

## Rule
```js
{
	"all": [
		{ // only customers without property SLA: yes
            "fact": "customer-propery",
            "params": {
                "key": "SLA"
            },
			"operator": "notEqual",
			"value": "yes"
		}{
            "any": [
                { // before working hours
                    "fact": "time",
                    "operator": "lessThan",
                    "value": 700 // 
                },{ // after working hours
                    "fact": "time",
                    "operator": "greaterThan",
                    "value": 1600
                },{ // 0 is sunday, 6 is saturday
                    "fact": "day-of-week",
                    "operator": "equal",
                    "value": 0
                },{ // 0 is sunday, 6 is saturday
                    "fact": "day-of-week",
                    "operator": "equal",
                    "value": 6
                }
            ]
        }
	]
}
```

## Fix
```js
{
    "destination": {
        "transport": { // set all notification methods to false
            "email": false,
            "sms": false,
            "ticket": false,
            "mobilepush": false,
            "bucket": false
        }
    }
}
```