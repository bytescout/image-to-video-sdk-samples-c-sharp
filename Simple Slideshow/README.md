## simple slideshow in C# and ByteScout Image To Video SDK

### Write code in C# to make simple slideshow with this How-To tutorial

The sample source codes on this page will demonstrate you how to make simple slideshow in C#. Simple slideshow in C# can be implemented with ByteScout Image To Video SDK. ByteScout Image To Video SDK is the SDK that is designed to generate video slideshow with 100+ 2d and 3D transition effects. Can generate WMV, AVI, WEBM video file with adjustable quality, framerate, output video size.

C# code snippet like this for ByteScout Image To Video SDK works best when you need to quickly implement simple slideshow in your C# application. Follow the instruction from the scratch to work and copy and paste code for C# into your editor. Enhanced documentation and tutorials are available along with installed ByteScout Image To Video SDK if you'd like to dive deeper into the topic and the details of the API.

Visit our website provides for free trial version of ByteScout Image To Video SDK. Free trial includes lots of source code samples to help you with your C# project.

## REQUEST FREE TECH SUPPORT

[Click here to get in touch](https://bytescout.zendesk.com/hc/en-us/requests/new?subject=ByteScout%20Image%20To%20Video%20SDK%20Question)

or just send email to [support@bytescout.com](mailto:support@bytescout.com?subject=ByteScout%20Image%20To%20Video%20SDK%20Question) 

## ON-PREMISE OFFLINE SDK 

[Get Your 60 Day Free Trial](https://bytescout.com/download/web-installer?utm_source=github-readme)
[Explore SDK Docs](https://bytescout.com/documentation/index.html?utm_source=github-readme)
[Sign Up For Online Training](https://academy.bytescout.com/)


## ON-DEMAND REST WEB API

[Get your API key](https://pdf.co/documentation/api?utm_source=github-readme)
[Explore Web API Documentation](https://pdf.co/documentation/api?utm_source=github-readme)
[Explore Web API Samples](https://github.com/bytescout/ByteScout-SDK-SourceCode/tree/master/PDF.co%20Web%20API)

## VIDEO REVIEW

[https://www.youtube.com/watch?v=FzPgeGFL8YA](https://www.youtube.com/watch?v=FzPgeGFL8YA)




<!-- code block begin -->

##### ****Program.cs:**
    
```
using System;
using System.Diagnostics;
using BytescoutImageToVideo;

namespace SimpleSlideshow
{
	class Program
	{
		static void Main(string[] args)
		{
			try
			{
            	Console.WriteLine("Converting JPG slides to video, please wait...");

				// Create BytescoutImageToVideoLib.ImageToVideo object instance
				ImageToVideo converter = new ImageToVideo();

				// Activate the component
				converter.RegistrationName = "demo";
				converter.RegistrationKey = "demo";

				// Add images and set the duration for every slide
				Slide slide;
				slide = converter.AddImageFromFileName("..\\..\\..\\..\\slide1.jpg");
				slide.Duration = 3000; // 3000ms = 3s
				slide = converter.AddImageFromFileName("..\\..\\..\\..\\slide2.jpg");
				slide.Duration = 3000;
				slide = converter.AddImageFromFileName("..\\..\\..\\..\\slide3.jpg");
				slide.Duration = 3000;

				// Set output video size
				converter.OutputWidth = 640;
				converter.OutputHeight = 480;

				// Set output video file name
				converter.OutputVideoFileName = "result.wmv";

				// Run the conversion
				converter.RunAndWait();

				// Release resources
				System.Runtime.InteropServices.Marshal.ReleaseComObject(converter);

				// Open the result video file in default media player
				Process.Start("result.wmv");

        		Console.WriteLine("Done. Press any key to continue..");
        		Console.ReadKey();
            }
            catch(Exception e)
			{
                Console.WriteLine("Error: " + e.ToString());
                Console.WriteLine("\nPress any key to exit.");
                Console.ReadKey();
            }
		}
	}
}

```

<!-- code block end -->    

<!-- code block begin -->

##### ****SimpleSlideshow.VS2005.csproj:**
    
```
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
    <ProductVersion>8.0.50727</ProductVersion>
    <SchemaVersion>2.0</SchemaVersion>
    <ProjectGuid>{8B6E5CBB-7E95-4598-990F-0496317A117D}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <AppDesignerFolder>Properties</AppDesignerFolder>
    <RootNamespace>SimpleSlideshow</RootNamespace>
    <AssemblyName>SimpleSlideshow</AssemblyName>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
    <DebugType>pdbonly</DebugType>
    <Optimize>true</Optimize>
    <OutputPath>bin\Release\</OutputPath>
    <DefineConstants>TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Xml" />
  </ItemGroup>
  <ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
  </ItemGroup>
  <ItemGroup>
    <COMReference Include="BytescoutImageToVideo">
      <Guid>{5212739C-A95B-4CDA-B116-F540A549B648}</Guid>
      <VersionMajor>1</VersionMajor>
      <VersionMinor>0</VersionMinor>
      <Lcid>0</Lcid>
      <WrapperTool>tlbimp</WrapperTool>
      <Isolated>False</Isolated>
      <EmbedInteropTypes>True</EmbedInteropTypes>
    </COMReference>
    <COMReference Include="stdole">
      <Guid>{00020430-0000-0000-C000-000000000046}</Guid>
      <VersionMajor>2</VersionMajor>
      <VersionMinor>0</VersionMinor>
      <Lcid>0</Lcid>
      <WrapperTool>primary</WrapperTool>
      <Isolated>False</Isolated>
    </COMReference>
  </ItemGroup>
  <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
  <!-- To modify your build process, add your task inside one of the targets below and uncomment it. 
       Other similar extension points exist, see Microsoft.Common.targets.
  <Target Name="BeforeBuild">
  </Target>
  <Target Name="AfterBuild">
  </Target>
  -->
</Project>
```

<!-- code block end -->    

<!-- code block begin -->

##### ****SimpleSlideshow.VS2008.csproj:**
    
```
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="3.5">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
    <ProductVersion>9.0.21022</ProductVersion>
    <SchemaVersion>2.0</SchemaVersion>
    <ProjectGuid>{8B6E5CBB-7E95-4598-990F-0496317A117D}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <AppDesignerFolder>Properties</AppDesignerFolder>
    <RootNamespace>SimpleSlideshow</RootNamespace>
    <AssemblyName>SimpleSlideshow</AssemblyName>
    <OldToolsVersion>2.0</OldToolsVersion>
    <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
    <DebugType>pdbonly</DebugType>
    <Optimize>true</Optimize>
    <OutputPath>bin\Release\</OutputPath>
    <DefineConstants>TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Xml" />
  </ItemGroup>
  <ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
  </ItemGroup>
  <ItemGroup>
    <COMReference Include="BytescoutImageToVideo">
      <Guid>{5212739C-A95B-4CDA-B116-F540A549B648}</Guid>
      <VersionMajor>1</VersionMajor>
      <VersionMinor>0</VersionMinor>
      <Lcid>0</Lcid>
      <WrapperTool>tlbimp</WrapperTool>
      <Isolated>False</Isolated>
      <EmbedInteropTypes>True</EmbedInteropTypes>
    </COMReference>
    <COMReference Include="stdole">
      <Guid>{00020430-0000-0000-C000-000000000046}</Guid>
      <VersionMajor>2</VersionMajor>
      <VersionMinor>0</VersionMinor>
      <Lcid>0</Lcid>
      <WrapperTool>primary</WrapperTool>
      <Isolated>False</Isolated>
    </COMReference>
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

<!-- code block end -->    

<!-- code block begin -->

##### ****SimpleSlideshow.VS2010.csproj:**
    
```
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="4.0">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
    <ProductVersion>
    </ProductVersion>
    <SchemaVersion>2.0</SchemaVersion>
    <ProjectGuid>{8B6E5CBB-7E95-4598-990F-0496317A117D}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <AppDesignerFolder>Properties</AppDesignerFolder>
    <RootNamespace>SimpleSlideshow</RootNamespace>
    <AssemblyName>SimpleSlideshow</AssemblyName>
    <OldToolsVersion>3.5</OldToolsVersion>
    <TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
    <DebugType>pdbonly</DebugType>
    <Optimize>true</Optimize>
    <OutputPath>bin\Release\</OutputPath>
    <DefineConstants>TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Xml" />
  </ItemGroup>
  <ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
  </ItemGroup>
  <ItemGroup>
    <COMReference Include="BytescoutImageToVideo">
      <Guid>{5212739C-A95B-4CDA-B116-F540A549B648}</Guid>
      <VersionMajor>1</VersionMajor>
      <VersionMinor>0</VersionMinor>
      <Lcid>0</Lcid>
      <WrapperTool>tlbimp</WrapperTool>
      <Isolated>False</Isolated>
      <EmbedInteropTypes>True</EmbedInteropTypes>
    </COMReference>
    <COMReference Include="stdole">
      <Guid>{00020430-0000-0000-C000-000000000046}</Guid>
      <VersionMajor>2</VersionMajor>
      <VersionMinor>0</VersionMinor>
      <Lcid>0</Lcid>
      <WrapperTool>primary</WrapperTool>
      <Isolated>False</Isolated>
    </COMReference>
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

<!-- code block end -->