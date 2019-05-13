# Create a new View

There are four kinds of following views in both Saposs WF and Aquarium:

- Root View.
- Administrator View.
- End-User View.
- Normal View.

For Saposs Aquarium, there's still more one template view:

- Template View.

First of all, you need to unzip the downloaded view project template and open it in Visual Studio. In order to create a new view, you need to create a new class which implements IView.

## Root View

Root View is also called Start View. This view will be shown for the first time at the startup time. It is simple to create this view. The following is sample code:

For Saposs WF:

``` csharp

[Export(typeof(IView))]
public class EntryView : IView
{
    private EntryForm form = new EntryForm();

    public bool IsDefault => false;

    public bool IsAdmin => true;

    public ViewTypes Type => ViewTypes.WForm;

    public string Title => "Entry View";

    public string Description => "This is a entry view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 2, 23);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.EntryView";

    public List<string> Dependencies => new List<string>();

    public object Get()
    {
        return form;
    }
}
```

For Saposs Aquarium:

``` csharp

[Export(typeof(IView))]
public class EntryView : IWebMvcView
{
    public bool IsDefault => false;

    public bool IsAdmin => true;

    public ViewTypes Type => ViewTypes.WebPage;

    public string Title => "Entry MVC View";

    public string Description => "This is a entry view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.EntryView";

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = "entry-view";

    public string TemplateName { get; set; } = "[YOUR_TEMPLATE_NAME]";

    public object Get()
    {
        return Utils.ReadAssemblyResourceFile<View>();
    }
}
```

When IsAdmin was set to true and IsDefault was set to false, this view will be called "Entry View". As above sample, we assume that "EntryForm" form was created in your view.

## Administrator View

Administrator View will be shown, after end-users clicked on the button "Go to Admin Page". The following is sample code to create this view:

For Saposs WF:

``` csharp

[Export(typeof(IView))]
public class AdminView : IView
{
    private AdminForm form = new AdminForm();

    public bool IsDefault => true;

    public bool IsAdmin => true;

    public ViewTypes Type => ViewTypes.WForm;

    public string Title => "Admin View";

    public string Description => "This is a admin view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 2, 23);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.AdminView";

    public List<string> Dependencies => new List<string>();

    public object Get()
    {
        return form;
    }
}
```

For Saposs Aquarium:

``` csharp

[Export(typeof(IView))]
public class AdminView : IWebMvcView
{
    public bool IsDefault => true;

    public bool IsAdmin => true;

    public ViewTypes Type => ViewTypes.WebPage;

    public string Title => "Admin MVC View";

    public string Description => "This is a admin view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.AdminView";

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = "admin-view";

    public string TemplateName { get; set; } = "[YOUR_TEMPLATE_NAME]";

    public object Get()
    {
        return Utils.ReadAssemblyResourceFile<View>();
    }
}
```

When IsAdmin was set to true and IsDefault was set to true, this view will be called "Administrator View". As above sample, we assume that "AdminForm" form was created in your view.

## End-User View

End-User View will be shown, after end-users clicked on the button "Go to Development Page". The following is sample code to create this view:

For Saposs WF:

``` csharp

[Export(typeof(IView))]
public class EndUserView : IView
{
    private EndUserForm form = new EndUserForm();

    public bool IsDefault => true;

    public bool IsAdmin => false;

    public ViewTypes Type => ViewTypes.WForm;

    public string Title => "End-User View";

    public string Description => "This is a end-user view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 2, 23);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.EndUserView";

    public List<string> Dependencies => new List<string>();

    public object Get()
    {
        return form;
    }
}
```

For Saposs Aquarium:

``` csharp

[Export(typeof(IView))]
public class EndUserView : IWebMvcView
{
    public bool IsDefault => true;

    public bool IsAdmin => false;

    public ViewTypes Type => ViewTypes.WebPage;

    public string Title => "Admin MVC End-User View";

    public string Description => "This is a end-user view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.EndUserView";

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = "enduser-view";

    public string TemplateName { get; set; } = "[YOUR_TEMPLATE_NAME]";

    public object Get()
    {
        return Utils.ReadAssemblyResourceFile<View>();
    }
}
```

When IsAdmin was set to false and IsDefault was set to true, this view will be called "End-User View". As above sample, we assume that "EndUserForm" form was created in your view.

## Normal View

Normal View will be called using Saposs APIs. The following is sample code to create this view:

For Saposs WF:

``` csharp

[Export(typeof(IView))]
public class NormalView : IView
{
    private NormalForm form = new NormalForm();

    public bool IsDefault => false;

    public bool IsAdmin => false;

    public ViewTypes Type => ViewTypes.WForm;

    public string Title => "Normal View";

    public string Description => "This is a normal view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 2, 23);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.NormalView";

    public List<string> Dependencies => new List<string>();

    public object Get()
    {
        return form;
    }
}
```

For Saposs Aquarium:

``` csharp

[Export(typeof(IView))]
public class NormalView : IWebMvcView
{
    public bool IsDefault => false;

    public bool IsAdmin => false;

    public ViewTypes Type => ViewTypes.WebPage;

    public string Title => "Normal MVC View";

    public string Description => "This is a normal view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.NormalView";

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = "normal-view";

    public string TemplateName { get; set; } = "[YOUR_TEMPLATE_NAME]";

    public object Get()
    {
        return Utils.ReadAssemblyResourceFile<View>();
    }
}
```

When IsAdmin was set to false and IsDefault was set to false, this view will be called "Normal View". As above sample, we assume that "NormalForm" form was created in your view.

## Template View

Template View is similar to Normal View except only for web application. The following is sample code to create this view:

``` csharp

[Export(typeof(IView))]
public class TemplateView : IWebMvcView
{
    public bool IsDefault => false;

    public bool IsAdmin => false;

    public ViewTypes Type => ViewTypes.MasterWebPage;

    public string Title => "Template MVC View";

    public string Description => "This is a template view.";

    public string Version => "Version 1.0.0";

    public DateTime CreatedDate => new DateTime(2019, 5, 11);

    public DateTime? UpdatedDate => null;

    public bool IsEnabled => true;

    public int Order => 2;

    public List<object> Deps => new List<object>();

    public string Name => "YourApp.Views.TemplateView";

    public List<string> Dependencies => new List<string>();

    public string Route { get; set; } = string.Empty;

    public string TemplateName { get; set; };

    public object Get()
    {
        return Utils.ReadAssemblyResourceFile<View>();
    }
}
```