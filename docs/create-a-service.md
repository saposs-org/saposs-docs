# Create a new Service

First of all, you need to unzip the downloaded view project template and open it in Visual Studio. In order to create a new service, you need to create a new class which implements IService. The following is sample code:

For Saposs WF:

``` csharp

[Export(typeof(IService))]
public class Service : IService
{
    public string Name => "YourApp.Services.NewService";

    public string Title => "New service";

    public string Description => "This is a new service.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 2, 23);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 3;

    public List<string> Dependencies => new List<string>();

    public object Execute(params object[] objs)
    {
        return 1;
    }
}
```

For Saposs Aquarium:


``` csharp

[Export(typeof(IService))]
public class Service : IWebMvcService
{
    public string Name => "YourApp.Services.NewMvcService";

    public string Title => "New service";

    public string Description => "This is a new service.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 3;

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = "default-service";

    public object Execute(params object[] objs)
    {
        return 1;
    }
}
```