# XamlFind

# Nuget Package

https://www.nuget.org/packages/XamlFind/

# To use the base_page class

Make your MainPage inherit from base_page and create a new namespace within your XAML with the name of your assembly for example: xmlns:d="clr-namespace:Player;assembly=Player" for my project with the namespace Player and then set the type of your page to d:base_page instead of ContentPage

# Querying XAML

Querying XAML is done with the underscore function or the find function, taking as parameters the parent XAML element and the query selector.

Currently the selector types that are supported are Element.class or .class or simply Element (Where Element is the name of the element in question and class is the class name and the dot is the query selector for class) StyleId is used to store the class which can be typed within XAML for example as 
```
<StackLayout StyleId=".class1.class2"></StackLayout> Or by using the add_class method.
```
Selectors can also be chained using the > arrow selector representing the immediate children or the space selector representning all children.

Extra spaces are not allowed so this is an example query selector: ```List<Element> elements = this._(".class1>Element.class2 .class3");```

Elements returned must then be cast into the approriate elements to be used for example ```List<Element> elements = this._("StackLayout.class1");```

Will return all StackLayouts with class class1

Then to use the StackLayouts do something like this
```
foreach(Element e in elements) {
    StackLayout s = (StackLayout)e;
    s.BackgroundColor = Color.Red;
}
```

# Copying Elements
```
StackLayout first = new StackLayout();

StackLayout copy = (StackLayout)this.copy(first);
```

# Todos:
  - Update to .NET MAUI (Still waiting for AbsoluteLayout to be supported by .NET MAUI)
  - Possibly conform better to HTML/CSS standards for example use StyleClass instead of StyleId for classes
  - Support more selectors
  - Organize code better and remove some functions
