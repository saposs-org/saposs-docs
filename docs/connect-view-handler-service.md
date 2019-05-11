# Connect View-Handler-Service

Saposs offers you a set of APIs to connect between view, handler and service together. The following is more details about them:

| API Function   |      Return Value      |  Description |
|----------|-------------|------|
| Utils.ExecuteView |  object(Form or User Control, etc...) | Execute a view from a specific view name/id.  |
| Utils.ExecuteTemplateView |  cshtml or html, etc... | Execute a template view from a specific view name/id.  |
| Utils.ExecuteMvcView |  cshtml or html, etc... | Execute a MVC view from a specific route.  |
| Utils.ExecuteHandler |    N/A   |  Execute a handler from a specific handler name/id.  |
| Utils.ExecuteMvcHandler |    N/A   |  Execute a MVC handler from a specific route.  |
| Utils.ExecuteMvcMultipleHandlers |    N/A   |  Execute multiple MVC handlers from a specific route.  |
| Utils.ExecuteService | object |  Execute a service from a specific service name/id and its parameters(optional). |
| Utils.ExecuteMvcService | object |  Execute a service from a specific route and its parameters(optional). |

For instance:

Connect to an existing view:

``` csharp
// Your view name comes from Name property when implementing IView.
var view = Utils.ExecuteView("[YOUR_VIEW_NAME]");
```

Connect to an existing template view:

``` csharp
// Your view name comes from Name property when implementing IView.
var templateView = Utils.ExecuteTemplateView("[YOUR_VIEW_NAME]");
```

Connect to an existing MVC view:

``` csharp
// Your view route comes from Route property when implementing IMvcView.
var mvcView = Utils.ExecuteMvcView("[YOUR_ROUTE]");
```

Connect to an existing handler:

``` csharp
// Your handler name comes from Name property when implementing IHandler.
Utils.ExecuteHandler("[YOUR_HANDLER_NAME]"); 
```

Connect to an existing MVC handler:

``` csharp
// Your handler route comes from Route property when implementing IMvcHandler.
Utils.ExecuteMvcHandler("[YOUR_ROUTE]"); 
```

Connect to multiple existing MVC handlers:

``` csharp
// Your handler route comes from Route property when implementing IMvcHandler.
Utils.ExecuteMultipleMvcHandlers("[YOUR_ROUTE]"); 
```

Connect to an existing service:

``` csharp
// Your service name comes from Name property when implementing IService.
var result = Utils.ExecuteService("[YOUR_SERVICE_NAME]"); 
```

Connect to an existing MVC service:

``` csharp
// Your service route comes from Route property when implementing IMvcervice.
var result = Utils.ExecuteService("[YOUR_ROUTE]"); 
```


### NOTES

Basically, Saposs Aquarium used route to locate Views, Handlers and Services automatically as well as connect between them together.