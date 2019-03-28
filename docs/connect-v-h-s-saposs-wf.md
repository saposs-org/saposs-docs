# Connect View-Handler-Service

Saposs offers you a set of APIs to connect between view, handler and service together. The following is details about them:

| API Function   |      Return Value      |  Description |
|----------|-------------|------|
| Utils.ExecuteView |  object(Form or User Control, etc...) | Execute a view from a specific view name/id.  |
| Utils.ExecuteHandler |    N/A   |  Execute a handler from a specific handler name/id.  |
| Utils.ExecuteService | object |  Execute a service from a specific service name/id. |

For instance:

Connect to an existing view:

``` csharp
// Your view name comes from Name property when implementing IView.
var view = Utils.ExecuteView("[YOUR_VIEW_NAME]");
```

Connect to an existing handler:

``` csharp
// Your handler name comes from Name property when implementing IHandler.
Utils.ExecuteHandler("[YOUR_HANDLER_NAME]"); 
```

Connect to an existing service:

``` csharp
// Your service name comes from Name property when implementing IService.
var result = Utils.ExecuteService("[YOUR_SERVICE_NAME]"); 
```
