# Convert a .NET Framework Project To .NET Core 3
This Visual Studio Extension converts a WPF application built with the .NET Framework to a .NET Core 3 application.

# Usage
Simply right-click your WPF project and select the "Convert Project to .NET Core 3" option.

![Convert Project to .NET Core 3](images/convert-to-core-menu.jpg)

# Details
When you convert your application, the extension will update your CSPROJ file to the new .NET Core SDK style format.

What it keeps:
- Maintains the project version (uses AssemblyVersion)
- Maintains all project references
- Maintains all items where the "Build Action" is Resource
- Maintains all NuGet packages (it deletes the packages.config file)
- Comments out all Assembly related attributes in the AssemblyInfo.cs file

# Example
#### .NET Framework csproj file
```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
    <ProjectGuid>{99C9E82C-C594-446D-AA59-8FFBC43AD226}</ProjectGuid>
    <OutputType>WinExe</OutputType>
    <AppDesignerFolder>Properties</AppDesignerFolder>
    <RootNamespace>NavigationParticipation</RootNamespace>
    <AssemblyName>NavigationParticipation</AssemblyName>
    <TargetFrameworkVersion>v4.5.2</TargetFrameworkVersion>
    <FileAlignment>512</FileAlignment>
    <ProjectTypeGuids>{60dc8134-eba5-43b8-bcc9-bb4bc16c2548};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
    <WarningLevel>4</WarningLevel>
    <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugType>pdbonly</DebugType>
    <Optimize>true</Optimize>
    <OutputPath>bin\Release\</OutputPath>
    <DefineConstants>TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="Microsoft.Practices.ServiceLocation, Version=1.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
      <HintPath>..\packages\CommonServiceLocator.1.3\lib\portable-net4+sl5+netcore45+wpa81+wp8\Microsoft.Practices.ServiceLocation.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="Microsoft.Practices.Unity, Version=4.0.0.0, Culture=neutral, PublicKeyToken=6d32ff45e0ccc69f, processorArchitecture=MSIL">
      <HintPath>..\packages\Unity.4.0.1\lib\net45\Microsoft.Practices.Unity.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="Microsoft.Practices.Unity.Configuration, Version=4.0.0.0, Culture=neutral, PublicKeyToken=6d32ff45e0ccc69f, processorArchitecture=MSIL">
      <HintPath>..\packages\Unity.4.0.1\lib\net45\Microsoft.Practices.Unity.Configuration.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="Microsoft.Practices.Unity.RegistrationByConvention, Version=4.0.0.0, Culture=neutral, PublicKeyToken=6d32ff45e0ccc69f, processorArchitecture=MSIL">
      <HintPath>..\packages\Unity.4.0.1\lib\net45\Microsoft.Practices.Unity.RegistrationByConvention.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="Prism, Version=6.2.0.0, Culture=neutral, PublicKeyToken=91a96d2a154366d8, processorArchitecture=MSIL">
      <HintPath>..\packages\Prism.Core.6.2.0\lib\net45\Prism.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="Prism.Unity.Wpf, Version=6.2.0.0, Culture=neutral, PublicKeyToken=91a96d2a154366d8, processorArchitecture=MSIL">
      <HintPath>..\packages\Prism.Unity.6.2.0\lib\net45\Prism.Unity.Wpf.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="Prism.Wpf, Version=6.2.0.0, Culture=neutral, PublicKeyToken=91a96d2a154366d8, processorArchitecture=MSIL">
      <HintPath>..\packages\Prism.Wpf.6.2.0\lib\net45\Prism.Wpf.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Windows.Interactivity, Version=4.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
      <HintPath>..\packages\Prism.Wpf.6.2.0\lib\net45\System.Windows.Interactivity.dll</HintPath>
      <Private>True</Private>
    </Reference>
    <Reference Include="System.Xml" />
    <Reference Include="Microsoft.CSharp" />
    <Reference Include="System.Core" />
    <Reference Include="System.Xml.Linq" />
    <Reference Include="System.Data.DataSetExtensions" />
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Xaml">
      <RequiredTargetFramework>4.0</RequiredTargetFramework>
    </Reference>
    <Reference Include="WindowsBase" />
    <Reference Include="PresentationCore" />
    <Reference Include="PresentationFramework" />
  </ItemGroup>
  <ItemGroup>
    <ApplicationDefinition Include="App.xaml">
      <Generator>MSBuild:Compile</Generator>
      <SubType>Designer</SubType>
    </ApplicationDefinition>
    <Page Include="Views\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
      <SubType>Designer</SubType>
    </Page>
    <Compile Include="App.xaml.cs">
      <DependentUpon>App.xaml</DependentUpon>
      <SubType>Code</SubType>
    </Compile>
    <Compile Include="Bootstrapper.cs" />
    <Compile Include="ViewModels\MainWindowViewModel.cs" />
    <Compile Include="Views\MainWindow.xaml.cs">
      <DependentUpon>MainWindow.xaml</DependentUpon>
      <SubType>Code</SubType>
    </Compile>
  </ItemGroup>
  <ItemGroup>
    <Compile Include="Properties\AssemblyInfo.cs">
      <SubType>Code</SubType>
    </Compile>
    <Compile Include="Properties\Resources.Designer.cs">
      <AutoGen>True</AutoGen>
      <DesignTime>True</DesignTime>
      <DependentUpon>Resources.resx</DependentUpon>
    </Compile>
    <Compile Include="Properties\Settings.Designer.cs">
      <AutoGen>True</AutoGen>
      <DependentUpon>Settings.settings</DependentUpon>
      <DesignTimeSharedInput>True</DesignTimeSharedInput>
    </Compile>
    <EmbeddedResource Include="Properties\Resources.resx">
      <Generator>ResXFileCodeGenerator</Generator>
      <LastGenOutput>Resources.Designer.cs</LastGenOutput>
    </EmbeddedResource>
    <None Include="packages.config" />
    <None Include="Properties\Settings.settings">
      <Generator>SettingsSingleFileGenerator</Generator>
      <LastGenOutput>Settings.Designer.cs</LastGenOutput>
    </None>
    <AppDesigner Include="Properties\" />
  </ItemGroup>
  <ItemGroup>
    <None Include="App.config" />
  </ItemGroup>
  <ItemGroup>
    <ProjectReference Include="..\ModuleA\ModuleA.csproj">
      <Project>{ab8b448c-dd74-4d60-a041-3e5d03a32180}</Project>
      <Name>ModuleA</Name>
    </ProjectReference>
  </ItemGroup>
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
  <!-- To modify your build process, add your task inside one of the targets below and uncomment it. 
       Other similar extension points exist, see Microsoft.Common.targets.
  <Target Name="BeforeBuild">
  </Target>
  <Target Name="AfterBuild">
  </Target>
  -->
</Project>
```

#### .NET Core 3 csproj file
```
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
    <AssemblyName>NavigationParticipation</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Prism.Unity" Version="7.2.0.639-ci" />
  </ItemGroup>
  <ItemGroup>
    <ProjectReference Include="..\ModuleA\ModuleA.csproj" />
  </ItemGroup>  
</Project>
```
