# SLA : enable notification

Enable notifications based on utc time, day of week and if the customer has a specific ```SLA``` property.

This sample expects that you have configured notifications and enables mobile messages.

## Rule
```js
{
	"all": [
		{ // only customers without property SLA: yes
            "fact": "customer-propery",
            "params": {
                "key": "SLA"
            },
			"operator": "equal",
			"value": "yes"
		},{ // only if it is a storage alert
			"fact": "agent-tags",
			"operator": "contains",
			"value": "storage"
		},{
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
        "transport": { // enable sms 
            "sms": true
        }
    }
}
```