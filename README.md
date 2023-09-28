# how-to-change-empty-view-at-run-time-in-.net-maui-listview

This demo shows about how to change empty view at run time in .NET MAUI ListView

## XAML 
  <ContentPage.Resources>
        <ResourceDictionary>
            <local:ListViewBoolToSortImageConverter x:Key="BoolToSortIconConverter"/>
            <ContentView x:Key="SingleView">
                <Label Text="No Items" FontSize="18" FontFamily="Roboto-Regular" 
                   TextColor="#666666" HorizontalTextAlignment="Center" VerticalOptions="CenterAndExpand"/>
            </ContentView>
            <ContentView x:Key="MultiView">
                <StackLayout VerticalOptions="CenterAndExpand" >
                    <Label Text="&#xe725;" FontSize="40" TextColor="#666666" Opacity="0.8"
                               FontFamily="{OnPlatform iOS=ListViewFontIcons, MacCatalyst=ListViewFontIcons, Android=ListViewFontIcons.ttf#, UWP=ListViewFontIcons.ttf#ListViewFontIcons}"
                               HorizontalTextAlignment="Center" VerticalTextAlignment="Center" />
                    <Label TextColor="#666666" Text="No Items" FontSize="16" FontFamily="Roboto-Regular" HorizontalTextAlignment="Center" VerticalTextAlignment="Center"  Margin="0,10,0,0"/>
                </StackLayout>
            </ContentView>

        </ResourceDictionary>
    </ContentPage.Resources>

    <ContentPage.BindingContext>
        <local:SortingFilteringViewModel x:Name="viewModel"/>
    </ContentPage.BindingContext>

    <ContentPage.Content>
        <Grid Margin="0">
            <Grid.RowDefinitions>
                <RowDefinition Height="30"/>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="30"/>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Label Grid.Row="0" Text="Inventory Management" TextColor="#E3000000" FontFamily="Roboto-Medium" CharacterSpacing="0.25" FontSize="16" Margin="8,10,0,0" />

            <Grid  x:Name="headerGrid" Grid.Row="1" Margin="8,16,8,16">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                ---
            <Grid Grid.Row="3" HeightRequest="30" IsVisible="{Binding IsVisible}" Margin="8,0,8,0">
                <Grid.ColumnDefinitions>                    
                    <ColumnDefinition Width="Auto"/>
                    <ColumnDefinition Width="Auto"/>
                    <ColumnDefinition Width="*"/>
                </Grid.ColumnDefinitions>
                <Label Text="Change EmptyView" FontSize="14" TextColor="#666666" FontFamily="Roboto-Regular" VerticalTextAlignment="Center"/>
                <CheckBox Grid.Column="1" x:Name="checkBox" IsChecked="False" Margin="5,0,0,0"/>
                <Label Grid.Column="2" Text="{Binding Text}" FontSize="14" TextColor="#666666" FontFamily="Roboto-Regular" VerticalTextAlignment="Center" Margin="10,0,0,0" HeightRequest="50"/>
            </Grid>

            <syncfusion:SfListView x:Name="listView" 
                       Grid.Row="4"
                       SelectionMode="None"                                     
                       ItemsSource="{Binding Items}"                      
                       ItemSize="56" EmptyView="{StaticResource SingleView}">             

                <syncfusion:SfListView.ItemTemplate>
                    ---
                </syncfusion:SfListView.ItemTemplate>
            </syncfusion:SfListView>
        </Grid>
## C#

private void CheckBox_CheckedChanged(object sender, CheckedChangedEventArgs e)
{
  if(e.Value)
    listView.EmptyView = Resources["MultiView"];
  else
    listView.EmptyView = Resources["SingleView"];
}

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.