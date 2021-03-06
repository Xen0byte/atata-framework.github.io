To get started, install [**Atata Templates**]({{ site.links.atata_templates }}) Visual Studio extension.

The extension provides the following templates:

- Project templates:
  - Atata NUnit Basic Test Project (.NET Core)
  - Atata NUnit Basic Test Project (.NET Framework)
  - Atata NUnit Advanced Test Project (.NET Core)
  - Atata Components Library (.NET Standard)
  - Atata Components Library (.NET Framework)
- Item templates:
  - Atata Page Object
  - Atata Base Page Object
  - Atata Control
  - Atata Trigger
  - Atata NUnit Test Fixture
  - Atata NUnit Base Test Fixture

#### Create Project

When extension is installed, you can create a project of one of Atata project types.
In Visual Studio:

1. Go to **File/New/Project...** or **File/Add/New Project...** (to add to existing solution)
1. Type **Atata** into search box or choose **Atata** in "project types" drop-down
1. Choose template (e.g.: **Atata NUnit Advanced Test Project (.NET Core)**) and specify project name and location

![Atata Templates project](/assets/images/atata-templates/new-project-window.png?v3)

#### Project References

The project is created with NuGet package references:

- {% include nuget.md name="Atata" %}
- {% include nuget.md name="Atata.WebDriverExtras" %}
- {% include nuget.md name="Atata.WebDriverSetup" %}
- {% include nuget.md name="Selenium.WebDriver" %}
- {% include nuget.md name="NUnit" %}
- {% include nuget.md name="NUnit3TestAdapter" %}
- {% include nuget.md name="Atata.Configuration.Json" %} (for advanced project)
- {% include nuget.md name="NLog" %} (for advanced project)

#### Configuration

You don't need to configure specific browser driver packages,
as a project is by default configured to automatically download appropriate driver,
by use of {% include nuget.md name="Atata.WebDriverSetup" %} package.

In the created project you can specify your testing site base URL and appropriate driver in
`SetUpFixture.cs` or `Atata.local.json` class, depending on type of project (basic or advanced).

```cs
AtataContext.GlobalConfiguration
    .UseChrome()
        .WithArguments("start-maximized")
    .UseBaseUrl("SITE_URL")
    //...
```

```js
{
  "baseUrl": "https://atata.io/"
  // Other environment specific configuration properties can be added here.
}
```

#### Test Fixtures

The created project also contains ready to use `SampleTests.cs` fixture, which can be either modified or removed:

```cs
using Atata;
using NUnit.Framework;

namespace AtataUITests1
{
    public class SampleTests : UITestFixture
    {
        [Test]
        public void SampleTest()
        {
            Go.To<OrdinaryPage>()
                .PageTitle.Should.Contain("Atata");
        }
    }
}
```

Further test fixture classes are recommended to inherit from `UITestFixture`,
or just choose "Atata NUnit Test Fixture" item template in "Add New Item Window".

#### Change .NET Version

By default, "Atata NUnit Basic Test Project (.NET Core)" and "Atata NUnit Advanced Test Project (.NET Core)"
project templates create a project with .NET Core 3.1 version.

To change the version to .NET 5 or another version:

1. Open project `.csproj` file.
1. Change the value of `<TargetFramework>` tag from `netcoreapp3.1` to `net5.0` or another one.
   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
   
     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>
   
     <!-- ... -->
   
   </Project>
   ```