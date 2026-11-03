# Useful Groovy


## Get Header & Property

```Groovy
def fileName = message.getHeader("CamelFileNameOnly", String) ?: "payload.txt"
// ou
def headers = message.getHeaders();
def value = headers.get("oldHeader");
message.setHeader("oldHeader", value + " modified");
message.setHeader("newHeader", "newHeader");

def sourceDirectory = message.getProperty("SourceDirectory") ?: "SourceDirectory"
// ou
def properties = message.getProperties();
value = properties.get("oldProperty");
message.setProperty("oldProperty", value + " modified");
message.setProperty("newProperty", "newProperty");
```

```Groovy
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

## Import v2
```Groovy
import com.sap.it.script.v2.api.Message;
```
