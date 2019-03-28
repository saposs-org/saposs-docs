# Create a new View

There are four kinds of following views in Saposs WF:

- Root View.
- Administrator View.
- End-User View.
- Normal View.

First of all, you need to unzip the downloaded view project template and open it in Visual Studio. In order to create a new view, you need to create a new class which implements IView.

## Root View

Root View is also called Start View. This view will be shown for the first time at the startup time. It is simple to create this view. The following is sample code:

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

When IsAdmin was set to true and IsDefault was set to false, this view will be called "Entry View". As above sample, we assume that "EntryForm" form was created in your view.

## Administrator View

Administrator View will be shown, after end-users clicked on the button "Go to Admin Page". The following is sample code to create this view:

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

When IsAdmin was set to true and IsDefault was set to true, this view will be called "Administrator View". As above sample, we assume that "AdminForm" form was created in your view.

## End-User View

End-User View will be shown, after end-users clicked on the button "Go to Development Page". The following is sample code to create this view:

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

When IsAdmin was set to false and IsDefault was set to true, this view will be called "End-User View". As above sample, we assume that "EndUserForm" form was created in your view.


## Normal View

Normal View will be called using Saposs APIs. The following is sample code to create this view:

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

When IsAdmin was set to false and IsDefault was set to false, this view will be called "Normal View". As above sample, we assume that "NormalForm" form was created in your view.
