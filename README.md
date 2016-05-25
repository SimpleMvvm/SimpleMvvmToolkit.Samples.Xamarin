# Simple MVVM Toolkit Express: Xamarin Forms Sample

1. To use this sample, instsall the *Xamarin tools for Visual Studio 2015*.
  - See here for details:
    + https://msdn.microsoft.com/en-us/library/mt613162.aspx
  - To overcome 2GB RAM limit see:
    + https://guido1993.wordpress.com/2015/05/05/how-to-overcome-the-2-gb-ram-limit-on-android-visual-studio-2015-emulators 
  - Using ReSharper from JetBrains will provide XAML intellisense for Xamarin Forms
  - To unlock the Android emulator, drag the lock icon on the screen upwards:
    + https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/visual-studio-android-emulator

2. Create a new Cross-Platform project using Visual Studio 2015 or higher
  - Target Framework: Xamarin.Forms Portable
  - Update NuGet packages
  - Build the solution

3. Add the SimpleMvvmToolkit.Express NuGet package to each project

4. Use Code Snippets Manager to add the Simple Mvvm C# code snippets

5. Add Models folder
  - Add Customer class
  - Use mvvmprop snippet to add properties
    + CustomerId, CustomerName, City

6. Add Services folder
  - Interface: ICustomerService
  - Class: MockCustomerService

7. Add ViewModels folder
  - MainPageViewModel
  - CustomerViewModel

8. Add Locators folder
  - Add NuGet package: SimpleInjector
  - Add ViewModelLocator class

9. Add ViewModelLocator to app resources
  - Remove existing App.cs file
  - Add new Forms Xaml Page named App.cs
  - Replace ContentPage with Application
  - Add a Resource for ViewModelLocator with the key "Locator"
  
  ```xml
  <?xml version="1.0" encoding="utf-8" ?>
  <Application xmlns="http://xamarin.com/schemas/2014/forms"
              xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
              xmlns:locators="clr-namespace:SimpleMvvmSamples.XamarinForms.Locators;assembly=SimpleMvvmSamples.XamarinForms"
              x:Class="SimpleMvvmSamples.XamarinForms.App">
    <Application.Resources>
      <ResourceDictionary>
        <locators:ViewModelLocator x:Key="Locator"/>
      </ResourceDictionary>
    </Application.Resources>
  </Application>
  ```  

10. Add Views folder
  - Add Forms Xaml Page: CustomerView
  - Add StackLayout with a BindingContext of MainPageViewModel
  - Add a Grid within the StackLayout with a BindingContext of CustomerViewModel

11. Build and deploy each target project
  - Clicking the New Customer button should populate the Entry controls