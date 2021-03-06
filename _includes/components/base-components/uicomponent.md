Represents the base class for UI components (page objects and controls).

When accessing any `UIComponent`'s and inherited type's member that uses `Scope` (actual HTML element) property, executes `TriggerEvents.BeforeAccess` and `TriggerEvents.AfterAccess` triggers. [Find out more on triggers](/triggers/).
{:.info}

#### Syntax

There are 2 `UIComponent` classes. The generic one is inherited from the non-generic:

```cs
public abstract class UIComponent
```

and 

```cs
public abstract class UIComponent<TOwner> : UIComponent, IUIComponent<TOwner>
    where TOwner : PageObject<TOwner>
```

`TOwner` is the type of the owner page object. Declaring any control or page object requires specifying `TOwner`.
{:.info}

#### Properties

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">IWebElement</span></span>
    <h3><span class="body">Scope</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `IWebElement` instance that represents the scope HTML element. Also executes `TriggerEvents.BeforeAccess` and `TriggerEvents.AfterAccess` triggers.

```cs
Component.Scope.SendKeys("some text");
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">UIComponentAttributeProvider</span><wbr>&lt;<span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">Attributes</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `UIComponentAttributeProvider<TOwner>` instance that provides an access to the scope element's attributes.

```cs
Component.Attributes.Class.Should.Contain("some-class");
Component.Attributes["data-value"].Should.Equal("val");
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">UIComponentCssProvider</span><wbr>&lt;<span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">Css</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `UIComponentCssProvider<TOwner>` instance that provides an access to the scope element's CSS properties.

```cs
Component.Css["display"].Should.Equal("block");
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">DataProvider</span><wbr>&lt;<span class="keyword">bool</span>, <span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">IsVisible</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `DataProvider<bool, TOwner>` instance for the value indicating whether the control is visible.

```cs
Component.IsVisible.Should.BeTrue();
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">DataProvider</span><wbr>&lt;<span class="keyword">string</span>, <span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">Content</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `DataProvider<string, TOwner>` instance for the text content.

```cs
Component.Content.Should.Contain("some value");
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">UIComponentVerificationProvider</span><wbr>&lt;<span class="type">UIComponent</span><wbr>&lt;<span class="type">TOwner</span>&gt;, <span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">Should</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the verification provider that gives a set of verification extension methods.

```cs
Component.Should.Exist();
Component.Should.Not.BeHidden();
Component.Should.BeDisabled();
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">UIComponentTriggerSet</span><wbr>&lt;<span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">Triggers</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the set of triggers. Provides the functionality to get/add/remove triggers dynamically.

```cs
Component.Triggers.Add(new WaitAttribute(2));
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">UIComponentLocationProvider</span><wbr>&lt;<span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">ComponentLocation</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `UIComponentLocationProvider<TOwner>` instance that provides an access to the scope element's location (X and Y).

```cs
Component.ComponentLocation.X.Should.BeGreater(10);
```

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">UIComponentSizeProvider</span><wbr>&lt;<span class="type">TOwner</span>&gt;</span>
    <h3><span class="body">ComponentSize</span><span class="tail"> { <span class="keyword">get</span>; }</span></h3>
</div>

Gets the `UIComponentSizeProvider<TOwner>` instance that provides an access to the scope element's size (Width and Height).

```cs
Component.ComponentSize.Height.Should.BeLessOrEqual(15);
```

#### Methods

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">IWebElement</span></span>
    <h3><span class="body">GetScope</span><span class="tail">(<span class="type">SearchOptions</span> options = <span class="keyword">null</span>)</span></h3>
</div>

Gets the `IWebElement` instance that represents the scope HTML element. Also executes `TriggerEvents.BeforeAccess` and `TriggerEvents.AfterAccess` triggers.

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="keyword">bool</span></span>
    <h3><span class="body">Exists</span><span class="tail">(<span class="type">SearchOptions</span> options = <span class="keyword">null</span>)</span></h3>
</div>

Determines whether the component exists. If `options` is set to null, then it uses `SearchOptions.Safely()`.

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="keyword">bool</span></span>
    <h3><span class="body">Missing</span><span class="tail">(<span class="type">SearchOptions</span> options = <span class="keyword">null</span>)</span></h3>
</div>

Determines whether the component is missing. If `options` is set to null, then it uses `SearchOptions.Safely()`.

<div class="member">
    <span class="head"><span class="keyword">public</span> <span class="type">TOwner</span></span>
    <h3><span class="body">Wait</span><span class="tail">(<span class="type">Until</span> until, <span class="type">WaitOptions</span> options = <span class="keyword">null</span>)</span></h3>
</div>

Waits until the specified component condition is met.

```cs
LoadingBlock.Wait(Until.Hidden);
// Or
ContentBlock.Wait(Until.Visible);
```