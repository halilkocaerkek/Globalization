# Globalization

```csharp
using System.Globalization;

var allCultures = CultureInfo.GetCultures(CultureTypes.AllCultures);
var invariantCulture = CultureInfo.InvariantCulture;

allCultures.AsEnumerable().ToList().ForEach(c =>
{
    if (c != invariantCulture)
    {
        if (c.Parent != null && c.Parent == invariantCulture)
        {
            Console.WriteLine( $"{c.DisplayName}, {c.Parent.DisplayName}");
        }

        var subCultures = allCultures.Where(s => s.Parent.DisplayName == c.DisplayName);
        if (subCultures.Any())
        {
            subCultures.ToList().ForEach(c => Console.WriteLine($"\t{c.DisplayName}, {c.EnglishName}, {c.NativeName}"));
        }
    }
});
```
