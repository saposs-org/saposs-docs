# Create a new Handler

First of all, you need to unzip the downloaded view project template and open it in Visual Studio. In order to create a new handler, you need to create a new class which implements IHandler. The following is sample code:

For Saposs WF:

``` csharp

[Export(typeof(IHandler))]
public class Handler : IHandler
{
    public string Name => "YourApp.Handlers.NewHandler";

    public string Title => "New Handler";

    public string Description => "...";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 2, 23);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<string> Dependencies => new List<string>();

    public void Execute()
    {
        // TODO: write code here...
    }
}
```

For Saposs Aquarium:


``` csharp

[Export(typeof(IHandler))]
public class Handler : IMvcHandler
{
    public string Name => "YourApp.Handlers.NewMvcHandler";

    public string Title => "New Handler";

    public string Description => "...";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = "default-handler"

    public void Execute()
    {
        // TODO: write code here...
    }
}
```