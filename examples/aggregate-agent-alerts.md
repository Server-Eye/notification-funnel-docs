# Aggregate agent alerts

This example sends email and ticket notifications, if all of the listet agents are in alert state. It is expected, that each agent has at least one notification with disabled transports.

Only the message and rsm of the last processed agent are dispatched to the transports. 

## Rule
```js
{
	"all": [
		{
			"fact": "agents-are-all-error",
			"params": {
				"agentIds": [
					"agent-id-1",
					"agent-id-2",
					"agent-id-n"
				]
			},
			"operator": "equal",
			"value": true
		}
	]
}
```

## Fix
```js
{
    "destination": {
        "transport": { // set all notification methods to false
            "email": true,
            "ticket": true
        }
    }
}
```