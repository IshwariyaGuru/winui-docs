---
layout: post
title: Backstage in WinUI Ribbon control | Syncfusion
description: Learn here all about Backstage support in Syncfusion WinUI Ribbon control with visibility support and more.
platform: winui
control: Ribbon
documentation: ug
---

# Backstage in WinUI Ribbon

The [RibbonBackstage](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.RibbonBackstage.html) allows you to host any controls to create a custom view based on the requirements of the application and it can be added by using the `Backstage` property. Backstage appears as the first tab in the top left corner named File and opens a backstage view when you click the `File` menu button. 

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon" BackstageMenuButtonContent="File">
    <ribbon:SfRibbon.Tabs>
        // Add ribbon tabs here...
    </ribbon:SfRibbon.Tabs>
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage Target="{Binding ElementName=rootGrid}">
            <Grid>
                <Grid.RowDefinitions>
                    <RowDefinition Height="*" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>
                <Grid
                    Grid.Row="0"
                    Padding="0,0,0,1"
                    VerticalAlignment="Top"
                    BorderBrush="LightGray"
                    BorderThickness="0,0,0,1">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="481" />
                    </Grid.RowDefinitions>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition />
                        <ColumnDefinition />
                    </Grid.ColumnDefinitions>
                    <TextBlock
                        Grid.Row="0"
                        Padding="15"
                        FontSize="24"
                        FontWeight="SemiBold"
                        Text="Settings" />
                    <StackPanel
                        Grid.Row="1"
                        Margin="15,15,15,0"
                        BorderBrush="LightGray"
                        BorderThickness="0,0,0,0">
                        <TextBlock
                            Padding="0,0,0,5"
                            FontSize="16"
                            Text="User Information" />
                        <TextBlock
                            Padding="0,5,0,5"
                            FontSize="14"
                            Text="Name : John" />
                        <HyperlinkButton Content="Change photo" />
                        <HyperlinkButton Content="Sign Out" />
                        <HyperlinkButton Content="Switch Account" />
                        <TextBlock Padding="0,5,0,5" Text="Theme Mode" />
                        <RadioButton Content="Light" />
                        <RadioButton Content="Dark" />
                        <RadioButton Content="Use system setting" />
                    </StackPanel>
                    <StackPanel
                        Grid.Row="1"
                        Grid.Column="1"
                        Padding="15,15,15,0"
                        BorderBrush="LightGray"
                        BorderThickness="1,0,0,0">
                        <TextBlock
                            Padding="0,0,0,5"
                            FontSize="16"
                            Text="Product Information" />
                        <HyperlinkButton Content="About product" />
                        <HyperlinkButton Content="Help" />
                        <HyperlinkButton Content="Updates" />
                    </StackPanel>
                </Grid>
                <StackPanel
                    Grid.Row="1"
                    Grid.ColumnSpan="2"
                    Padding="120,0,5,5"
                    HorizontalAlignment="Right"
                    BorderBrush="LightGray"
                    BorderThickness="0,0,0,0"
                    Orientation="Horizontal">
                    <Button
                        Margin="5"
                        Content="Options"
                        CornerRadius="0" />
                    <Button
                        Margin="5"
                        Content="Exit Backstage"
                        Click="Button_Click"
                        CornerRadius="0" />
                </StackPanel>
            </Grid>                           
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>                    
</ribbon:SfRibbon>
{% endhighlight %}
{% highlight c# %}
private void Button_Click(object sender, RoutedEventArgs e)
{
    this.ribbon.IsBackstageOpen = false;
}
{% endhighlight %} 
{% endtabs %}

![Hosting of custom controls in Ribbon backstage](Backstage-images/Backstage-image9.gif)

### Backstage button visibility

Ribbon allows you to show or hide a backstage menu button using the [ShowBackstageMenuButton](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.SfRibbon.html#Syncfusion_UI_Xaml_Ribbon_SfRibbon_ShowBackstageMenuButton) property.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon ShowBackstageMenuButton="False">
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home" />
        <ribbon:RibbonTab Header="Insert" />
        <ribbon:RibbonTab Header="View" />
    </ribbon:SfRibbon.Tabs>
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView />
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon> 
{% endhighlight %} 
{% endtabs %}

![Customize the backstage visibility](Backstage-images/Backstage-image8.png)

### Backstage view visibility

The Ribbon allows you to show or hide a backstage view visibility using the `IsBackstageOpen` property. 

* Through property

You can directly enable or disable the visibility of backstage view by setting value to the `IsBackstageOpen` property of Ribbon.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon"
                 IsBackstageOpen="True">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            </ribbon:BackstageView/>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %}
{% endtabs %}

* Through back button click event

You can open or close the backstage view dynamically using `BackButtonClick` event.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView x:Name="backstageview"
                                  BackButtonClick="BackstageView_BackButtonClick">
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% highlight c# %}
private void BackstageView_BackButtonClick(BackstageView sender, object args)
{
    this.ribbon.IsBackstageOpen = false;
}
{% endhighlight %} 
{% endtabs %}

* Through back button command

You can open or close the backstage view dynamically using `BackButtonCommand` property.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView x:Name="backstageview"
                                  BackButtonCommand="{x:Bind ButtonCommand}"
                                  BackButtonCommandParameter="false" />
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% highlight c# %}
public ICommand ButtonCommand { get; set; }
this.ButtonCommand = new DelegateCommand(ExecuteButtonCommand, CanExecuteCommand);

private bool CanExecuteCommand(object obj)
{
    return true;
}

private void ExecuteButtonCommand(object obj)
{
    this.ribbon.IsBackstageOpen = bool.Parse(obj.ToString());
}
{% endhighlight %} 
{% endtabs %}

## Host Backstage view to the RibbonBackstage

Ribbon provides the [BackstageView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageView.html) as separate view like in MSOutlook, MSWord applications, that can be hosted inside the ribbon backstage. The backstage view contains tabs and buttons, and separators are placed between backstage view items to create groups and it can be added using `Items` property. The view can be placed at the top or bottom of the application.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon>
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home" />
        <ribbon:RibbonTab Header="Insert" />
        <ribbon:RibbonTab Header="View" />
        <ribbon:RibbonTab Header="Layout" />
    </ribbon:SfRibbon.Tabs>
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView>
                <ribbon:BackstageView.Items>
                    <ribbon:BackstageViewTabItem Header="New" />
                    <ribbon:BackstageViewTabItem Header="Open" />
                    <ribbon:BackstageViewItemSeparator />
                    <ribbon:BackstageViewTabItem Header="Info" />
                    <ribbon:BackstageViewButtonItem Header="Save" />
                    <ribbon:BackstageViewButtonItem Header="Close" />
                </ribbon:BackstageView.Items>
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![Adding BackstageView to the RibbonBackstage](Backstage-images/Backstage-image1.png)


### Back button visibility

The [BackstageView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageView.html) allows you to show or hide the back button using `ShowBackButton` property. 

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView ShowBackButton="False" />
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![Customize the back button visibility](Backstage-images/Backstage-image2.png)

## Add BackstageViewTabItem

The [BackstageViewTabItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageViewTabItem.html) can be added to the backstage view and provide a separate view of the backstage when you click on the tab item. You can use the Header property to provide a name to the tab.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon>
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView>
                <ribbon:BackstageView.Items>
                    <ribbon:BackstageViewTabItem Header="New">
                    </ribbon:BackstageViewTabItem>
                    <ribbon:BackstageViewTabItem Header="Open">
                    </ribbon:BackstageViewTabItem>
                </ribbon:BackstageView.Items>
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![Adding BackstageViewTabItem to the BackstageView](Backstage-images/Backstage-image3.png)

## Add BackstageViewButtonItem

The [BackstageViewButtonItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageViewButtonItem.html) can be added to the backstage view that performs the actions of the `Click` event. You can also use the Command instead of Click Event, and the buttons with the name Save and Close are added using the `Content` property.


{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView>
                <ribbon:BackstageView.Items>
                    <ribbon:BackstageViewButtonItem Header="Save" />
                    <ribbon:BackstageViewButtonItem Header="Close"
                                                    Click="BackstageViewButtonItem_Click" />
                </ribbon:BackstageView.Items>
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% highlight c# %}
 private void BackstageViewButtonItem_Click(object sender, RoutedEventArgs e)
        {
            this.ribbon.IsBackstageOpen = false;
            ContentDialog contentDialog1 = new ContentDialog();
            contentDialog1.Title = "Backstage closed";
            contentDialog1.PrimaryButtonText = "Close";
            await contentDialog1.ShowAsync();
        }
{% endhighlight %} 
{% endtabs %}

![Adding BackstageViewButtonItem to the BackstageView](Backstage-images/Backstage-image4.png)

## Add BackstageViewItemSeparator

The [BackstageViewItemSeparator](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageViewItemSeparator.html) displays a line used to separate the backstage view items such as tabs and buttons. The separator can be added to backstage view for the following code snippet.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView>
                <ribbon:BackstageView.Items>
                    <ribbon:BackstageViewTabItem Header="New" />
                    <ribbon:BackstageViewTabItem Header="Open" />
                    <ribbon:BackstageViewItemSeparator />
                    <ribbon:BackstageViewTabItem Header="Info" />
                    <ribbon:BackstageViewButtonItem Header="Save" />
                    <ribbon:BackstageViewButtonItem Header="Close" />
                </ribbon:BackstageView.Items>
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![Adding BackstageViewItemSeparator to the BackstageView](Backstage-images/Backstage-image5.png)

## Add FooterItems to the BackstageView

The [BackstageView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageView.html) allows you to add footer items using `FooterItems` property and the backstage items can be added to the footer of backstage view for the following code snippet.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView>
                <ribbon:BackstageView.Items>
                    <ribbon:BackstageViewTabItem Header="New" />
                    <ribbon:BackstageViewTabItem Header="Open" />
                </ribbon:BackstageView.Items>
                <ribbon:BackstageView.FooterItems>
                    <ribbon:BackstageViewItemSeparator />
                    <ribbon:BackstageViewTabItem Header="Account" />
                    <ribbon:BackstageViewTabItem Header="Feedback" />
                    <ribbon:BackstageViewButtonItem  Header="Option" />
                </ribbon:BackstageView.FooterItems>
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![Adding FooterItems to the BackstageView](Backstage-images/Backstage-image6.png)

## Setting Icon to the BackstageView Items

BackstageView items such as [BackstageViewTabItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageViewTabItem.html) and [BackstageViewButtonItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.BackstageViewButtonItem.html) and tabs can display an icon as graphical content using the `Icon` property

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
    <ribbon:SfRibbon.Backstage>
        <ribbon:RibbonBackstage>
            <ribbon:BackstageView>
                <ribbon:BackstageView.Items>
                    <ribbon:BackstageViewTabItem Header="New"
                                                 Icon="NewFolder" />
                    <ribbon:BackstageViewTabItem Header="Open"
                                                 Icon="OpenWith" />
                    <ribbon:BackstageViewItemSeparator />
                    <ribbon:BackstageViewButtonItem Header="Save"
                                                    Icon="Save" />
                    <ribbon:BackstageViewButtonItem Header="Close"
                                                    Icon="Cancel" />
                </ribbon:BackstageView.Items>
                <ribbon:BackstageView.FooterItems>
                    <ribbon:BackstageViewItemSeparator />
                    <ribbon:BackstageViewTabItem Header="Account" />
                    <ribbon:BackstageViewTabItem Header="Feedback" />
                    <ribbon:BackstageViewButtonItem  Header="Option" />
                </ribbon:BackstageView.FooterItems>
            </ribbon:BackstageView>
        </ribbon:RibbonBackstage>
    </ribbon:SfRibbon.Backstage>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![Setting Icon to the BackstageView items](Backstage-images/Backstage-image7.png)

N> You can also use other icons types such as   [BitmapIcon](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.controls.bitmapicon?view=winui-3.0-preview), [FontIcon](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.controls.fonticon?view=winui-3.0-preview), [PathIcon](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.controls.pathicon?view=winui-3.0-preview) and [SymbolIcon](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.controls.symbolicon?view=winui-3.0-preview) to the backstage view items.
