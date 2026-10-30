# Useful Groovy


## Get Header & Property

```Groovy
def fileName = message.getHeader("CamelFileNameOnly", String) ?: "payload.txt"
def sourceDirectory = message.getProperty("SourceDirectory") ?: "SourceDirectory"
```

```Groovy
message.setProperty("isValid", isValid)
```

## Custom Header & property

```Groovy
package script.v2
import com.sap.it.script.v2.api.Message
def Message processData(Message message) {
    // ...
    def messageLog = messageLogFactory.getMessageLog(message);
    if(messageLog != null){
        messageLog.addCustomHeaderProperty("fileName", fileName)
    }
    return message
}
```

```Groovy

```
