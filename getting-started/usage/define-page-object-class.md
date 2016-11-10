```cs
using Atata;
using _ = SampleApp.AutoTests.SignInPage;

namespace SampleApp.AutoTests
{
    [VerifyTitle]
    [VerifyH1]
    [NavigateTo("signin")]
    public class SignInPage : Page<_>
    {
        public TextInput<_> Email { get; private set; }

        public PasswordInput<_> Password { get; private set; }

        public Button<_> SignIn { get; private set; }
    }
}
```

`SignInPage` is marked with several attributes:

* `[VerifyTitle]` - upon page initialization the check if the page title is equal to "Sign In - Atata Sample App" is conducted. "Sign In" value is taken from the class type name while ignoring "Page" word and formatted with Title case. The second part is taken from global `[assembly: VerifyTitleSettings(Format = "{0} - Atata Sample App")]` settings attribute.
* `[VerifyH1]` - upon page initialization the check if the page contains `<h1>` HTML element with "Sign In" text is conducted.
* `[NavigateTo("signin")]` - sets the relative URL of the page to be navigated to.