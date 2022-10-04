# Callbacks

## Pool-related notifications

You can set up this feature in SPO console > Manage pool > tab "Config". 

Note: If you want to deactivate this feature, update your callback url to empty and submit.

Notification structure what your script will receive (POST RAW body - json-encoded array) : 
```json
{
  "pool" : "pool1..........",
  "type" : "type",
  "message" : "human friendly message",
  "url" : "for block ie we send https://cexplorer.io/block/blockId"
}
  
```

### Available types:
- test - for internal purposes only; you should ignore this type; but, we can send callback with this type to verify if is your url valid and working (as Compatibility) - if returns "ok" output :-) 
- epoch - pool results after epoch transition
- delegation - new delegator
- undelegation - outgoing delegator
- stake - live stake change
- update - poolcert change
- block - new block
- offrelay - relay is offline
- onrelay - relay is back online
- award - received new reward (like first 100 blocks)

### Compatibility

Your callback script must return always pure text output simply "ok" (as we can remove old/notworking callback without this)
```text
ok
```
