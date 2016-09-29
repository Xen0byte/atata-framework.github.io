Represents the number input control. By default is being searched by the label. Handles any `input` element with `type="number"`, `type="tel"`, `type="text"` or without the type attribute defined.

```html
<input type="number" id="amount">
```
```cs
using Atata;
using _ = SampleApp.SamplePage;

namespace SampleApp
{
    public class SamplePage : Page<_>
    {
        [FindById]
        public NumberInput<_> Amount { get; private set; }
    }
}
```
```cs
Go.To<SamplePage>().
    Amount.Should.BeNull().
    Amount.Set(25).
    Amount.Should.Equal(25).
    Amount.Should.BeInRange(20, 30);
```

Supports `[Format]`, `[Culture]` and `[RandomizeNumberSettings]` settings attributes.
{:class="info"}