It is more custom approach to create Atata testing project. To get started just add [**Atata NuGet package**]({{ site.links.atata_nuget }}) to the project of **Class Library** type.

<code class="language-nugetpm">
PM> Install-Package Atata
</code>

The **Atata** package depends on the following packages (that are added automatically):

- {% include nuget.md name="Selenium.WebDriver" %}
- {% include nuget.md name="Selenium.Support" %}
* [Atata.WebDriverExtras]({{ site.links.atata_webdriverextras_nuget }})

You might also need to install a driver package for specific browser: {% include nuget.md name="WebDriver.ChromeDriver.win32" %}, {% include nuget.md name="WebDriver.IEDriverServer.win32" %}, etc.
{:.warning}

You are also free to select any test engine framework like: NUnit, Xunit, MSTest, etc.