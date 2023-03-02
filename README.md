Clone of "Modern UI (Metro) Charts for Windows 8, WPF, Silverlight": http://modernuicharts.codeplex.com/


Note:

Do not clone into a folder with the name "De.TortenMandelkow.MetroChart" in the path. The build script in XAMLReplace.targets (line 72) uses the path to determine which files to process for assembly name replacement and causes build to fail. 

###Relevant changes:
* `ChartSeries` now has a `BrushMember` property, allowing the chart piece color to be set via data member rather than palette.

####Usage:
Instead of [setting a custom palette](http://modernuicharts.codeplex.com/wikipage?title=Custom%20Color%20Palette) via the `Palette` property add a `Brush` member to the datapoint class used in the chart.
```C#
public class TestClass
{
    public string Category { get; set; }
    public int Number  { get; set; }
    public Brush Brush { get; set; } // <--
}
```
Then add that member to the ChartSeries xaml
```XAML
<chart:ChartSeries
    SeriesTitle="Errors"
    DisplayMember="Category"
    ValueMember="Number"
    BrushMember="Brush" // <--
    ItemsSource="{Binding Path=Errors}" />
```
See [Original documentation](http://modernuicharts.codeplex.com/documentation) for reference.
