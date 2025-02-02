---
layout: post
title: Getting Started with WinUI Time Picker control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Time Picker control, its elements, and more.
platform: WinUI
control: SfTimePicker
documentation: ug
---

# Getting Started with WinUI Time Picker

This section explains the steps required to add the [WinUI Time Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html) control and its time selection options. This section covers only basic features needed to get started with Syncfusion `Time Picker` control.

## Structure of Time Picker control

![Structure of WinUI Time Picker control](Getting-Started_images/Structure.png)

## Creating an application with WinUI Time Picker

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfTimePicker` control.

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:editors="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid Name="grid">
        <!--Adding Time Picker control -->
        <editors:SfTimePicker Name="sfTimePicker"/>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

using Syncfusion.UI.Xaml.Editors;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the Time Picker control
            SfTimePicker sfTimePicker = new SfTimePicker();

            grid.Children.Add(sfTimePicker);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![Time Picker control added in the application](Getting-Started_images/TimePicker_Added.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/Getting_Started)

## Select time programmatically

You can set or change the selected time programmatically by using [SelectedTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_SelectedTime) property. If you not assign any value for the `SelectedTime` property, `Time Picker` will automatically assign the current system time as `SelectedTime`.

{% tabs %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.SelectedTime = new DateTimeOffset(new DateTime(2021, 10, 29, 10, 45, 10));

{% endhighlight %}
{% endtabs %}

![Time Picker displaying the selected time](Getting-Started_images/SelectedTime.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Select time interactively

You can change the selected time interactively by enter the time value using keyboard or from the drop down time spinner. You can get the selected time from the `SelectedTime` property.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();

{% endhighlight %}
{% endtabs %}

![Time Picker displaying selected value](Getting-Started_images/selectedTimeinteratct.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/Getting_Started)

## Setting null value

If you want to set null value for the `Time Picker`, set the [AllowNullValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_AllowNullValue) property as `true` and set `SelectedTime` property as `null`. If `AllowNullValue` property is `false`, then the current system time is updated in `SelectedTime` property and displayed instead of `null`.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker SelectedTime="{x:Null}"
                      AllowNullValue="True"
                      Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.SelectedTime = null;
sfTimePicker.AllowNullValue = true;

{% endhighlight %}
{% endtabs %}

![Time Picker displaying the null value](Getting-Started_images/AllowNullValue.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Setting watermark text

You can prompt the user with some information by using the [PlaceHolderText](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_PlaceHolderText) property. This will be displayed only when the `Time Picker` contains the `SelectedTime` property as `null` and `AllowNullValue` property as `true`. If `AllowNullValue` property is `false`, then the current system time is updated in `SelectedTime` property and displayed instead of `PlaceHolderText`.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker PlaceHolderText="Select the Time"
                      SelectedTime="{x:Null}"
                      AllowNullValue="True"
                      Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.PlaceHolderText = "Select the Time";
sfTimePicker.SelectedTime = null;
sfTimePicker.AllowNullValue = true;

{% endhighlight %}
{% endtabs %}

![Time Picker displaying watermark text](Getting-Started_images/PlaceHolderText.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Time changed notification

You will be notified when selected time changed in `Time Picker` by using [TimeChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_TimeChanged) event. The `TimeChanged` event contains the old and newly selected time in the [OldDateTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SelectedDateTimeChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_SelectedDateTimeChangedEventArgs_OldDateTime) and [NewDateTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SelectedDateTimeChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_SelectedDateTimeChangedEventArgs_NewDateTime) properties.

* `OldDateTime` - Gets a time which is previously selected.
* `NewDateTime` - Gets a time which is currently selected.

{% tabs %}
{% highlight XAML %}

<editors:SfTimePicker TimeChanged="SfTimePicker_TimeChanged" 
                      Name="sfTimePicker"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.TimeChanged += SfTimePicker_TimeChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfTimePicker_TimeChanged(DependencyObject d, DependencyPropertyChangedEventArgs e) {          
    Console.WriteLine("The previously selected Time: " + e.OldDateTime.ToString());
    Console.WriteLine("The newly selected Time: " + e.NewDateTime.ToString());            
}

{% endhighlight %}
{% endtabs %}

## Cancel a time that is being changed

The `TimeChanging` event will be triggered as soon as a date is selected but before `SelectedTime` property is updated. If the change is considered invalid, it can be canceled. The `TimeChanging` event contains the following properties.

* `OldTime` - Gets a time which is previously selected.
* `NewTime` - Gets a time which is currently selected.
* `Cancel` - Gets or sets whether to cancel the selected time value update.

Users are restricted to select a blackout time from dropdown, however user can give text input through editor. As selecting a blackout time leads to crash, we can cancel the change using `TimeChanging` event.

N> `TimeChanging` event is called before the `TimeChanged` event when a time is selected.

{% tabs %}
{% highlight XAML %}

<editor:SfTimePicker Height="35" Width="150" TImeChanging="SfTimePicker_TimeChanging" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.TimeChanging += SfTimePicker_TimeChanging;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

 private void SfTimePicker_TimeChanging(object sender, Syncfusion.UI.Xaml.Editors.TimeChangingEventArgs e)
{
    var OldTime = e.OldTime;
    var NewTime = e.NewTime;

    //Cancel Selected time update
    e.Cancel = true;
}

{% endhighlight %}
{% endtabs %}


## Change time display format

 You can edit and display the selected time with various formatting like hour, minutes, seconds and meridiem formats by using the [FormatString](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_FormatString) property. The default value of `FormatString` property is `hh:mm tt`.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker x:Name="sfTimePicker" 
                      FormatString="HH:mm"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.FormatString= "HH:mm";

{% endhighlight %}
{% endtabs %}

![Time Picker selected time with hour and meridiem](Getting-Started_images/FormatString.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Restrict time selection

You can restrict the users from selecting a time within the particular range by specifying [MinTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_MinTime) and [MaxTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_MaxTime) properties in `Time Picker` control. The default value of `MinTime` property is `1/1/0001 12:00:00 AM` and `MaxTime` property is `12/31/9999 11:59:59 PM`.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker x:Name="sfTimePicker"/>

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.MinTime = new DateTimeOffset(new DateTime(2020, 12, 10, 4, 00, 00));
sfTimePicker.MaxTime = new DateTimeOffset(new DateTime(2020, 12, 10, 6, 59, 59));

{% endhighlight  %}
{% endtabs %}

![Time Picker restrict the time selection with particular range](Getting-Started_images/MinMaxTime.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Block times using BlackoutTimes

If you want to block particular times from the time selection, then add that times into the [BlackoutTimes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_BlackoutTimes) collection. You can add more block out times to the `BlackoutTimes` collection. The default value of `BlackoutTimes` property is `null`.

{% tabs %}
{% highlight c# %}

public class ViewModel
{       
    public DateTimeOffset? SelectedTime { get; set; }
    public DateTimeOffsetCollection BlackoutTimes { get; set; }
    public ViewModel()
    {
        SelectedTime = DateTimeOffset.Now.Date;
        BlackoutTimes = new DateTimeOffsetCollection();
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 0, 3, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 0, 58, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 1, 0, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 3, 0, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 9, 0, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 10, 0, 0, DateTimeOffset.Now.Offset));
    }
}

{% endhighlight  %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker SelectedTime="{Binding SelectedTime}" 
                      BlackoutTimes="{Binding BlackoutTimes}"
                      x:Name="sfTimePicker">
    <editors:SfTimePicker.DataContext>
        <local:ViewModel/>
    </editors:SfTimePicker.DataContext>
</editors:SfTimePicker>

{% endhighlight  %}
{% highlight C# %}

sfTimePicker.DataContext = new ViewModel();
sfTimePicker.SelectedTime = (sfTimePicker.DataContext as ViewModel).SelectedTime;
sfTimePicker.BlackoutTimes = (sfTimePicker.DataContext as ViewModel).BlackoutTimes;

{% endhighlight  %}
{% endtabs %}

![Time Picker blocks the particular times from selection](Getting-Started_images/Blackouttimes.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Edit time using free form editing

By default, the user entering each input numbers are automatically validated with the `FormatString`'s formats and assigned the proper value for current field, then it will move to next input field of the time format.

![Time Picker enables mask editing mode to select time](Getting-Started_images/Mask_Editingmode.gif)

If you want to perform the validation after the user completely entering their time inputs, use the [EditMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_EditMode) property value as `Normal`. Then the entered time value is validated with the `FormatString` property value by pressing the `Enter` key or lost focus. If entered value is not suit with `FormatString` property, the previously selected time value sets to `SelectedTime` property.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker EditMode="Normal"
                      x:Name="sfTimePicker" />

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.EditMode = DateTimeEditingMode.Normal;

{% endhighlight  %}
{% endtabs %}

![Time Picker enables free form editing to select time](Getting-Started_images/editmode_Normal.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

