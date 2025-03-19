# Create the unit test project

From the command line, create a folder for your test project, change into it, and then create the project using dotnet new:

```shell
$ mkdir MyFirstUnitTests
$ cd MyFirstUnitTests
$ dotnet new xunit3
The template "xUnit.net v3 Test Project" was created successfully.

Processing post-creation actions...
Restoring /.../MyFirstUnitTests/MyFirstUnitTests.csproj:
  Determining projects to restore...
  Restored /.../MyFirstUnitTests/MyFirstUnitTests.csproj (in 1.48 sec).
Restore succeeded.
```

The generated project file should look something like this:

```csharp
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
    <OutputType>Exe</OutputType>
    <RootNamespace>MyFirstUnitTests</RootNamespace>
    <TargetFramework>net8.0</TargetFramework>
    <!--
    To enable the Microsoft Testing Platform 'dotnet test' experience, add property:
      <TestingPlatformDotnetTestSupport>true</TestingPlatformDotnetTestSupport>

    To enable the Microsoft Testing Platform native command line experience, add property:
      <UseMicrosoftTestingPlatformRunner>true</UseMicrosoftTestingPlatformRunner>

    For more information on Microsoft Testing Platform support in xUnit.net, please visit:
      https://xunit.net/docs/getting-started/v3/microsoft-testing-platform
    -->
  </PropertyGroup>

  <ItemGroup>
    <Content Include="xunit.runner.json" CopyToOutputDirectory="PreserveNewest" />
  </ItemGroup>

  <ItemGroup>
    <Using Include="Xunit" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.12.0" />
    <PackageReference Include="xunit.v3" Version="1.0.0" />
    <PackageReference Include="xunit.runner.visualstudio" Version="3.0.0" />
  </ItemGroup>

</Project>
```

Let’s quickly review what’s in this project file:

- ImplicitUsings enables implicit using statements in your project. In addition to the default set of implicit using statements, you can see below that we’ve added an implicit using for the Xunit namespace where the most common xUnit.net types come from.
More information about implicit usings

- Nullable is enabled in this default template. Our libraries including nullable annotations to help you find when you may be accidentally dealing with null values. For example, Assert.NotNull is decorated in such a way that the compiler knows, if this assertion did not fail, then the value passed to it is known to not be null.
More information about nullable reference types

- OutputType is set to Exe, because unit test projects in xUnit.net v3 are stand-alone executables that can be directly run. We will see examples of this later in this document.
More information about xUnit.net v3 and stand-alone executables

- TargetFramework is set to net8.0 (which is the latest LTS build as of the writing of this document).
More information about target frameworks

- We have included an xunit.runner.json file in your project by default. You can edit this file and place configuration values into it.
More information about xUnit.net configuration files

- We have included three package references:
  - xunit.v3 is the core package needed to write unit tests for xUnit.net v3
  - xunit.runner.visualstudio and Microsoft.NET.Test.Sdk are used to enable support for dotnet test and Visual Studio Test Explorer

A single unit test was also generated (UnitTest1.cs in this example):

```csharp
namespace MyFirstUnitTests;

public class UnitTest1
{
    [Fact]
    public void Test1()
    {
        Assert.True(true);
    }
}
```

Now let’s verify that everything is working by running our tests with `dotnet run`:

```shell
$ dotnet run
xUnit.net v3 In-Process Runner v1.0.0+fd19795321 (64-bit .NET 8.0.8)
  Discovering: MyFirstUnitTests
  Discovered:  MyFirstUnitTests
  Starting:    MyFirstUnitTests
  Finished:    MyFirstUnitTests
=== TEST EXECUTION SUMMARY ===
   MyFirstUnitTests  Total: 1, Errors: 0, Failed: 0, Skipped: 0, Not Run: 0, Time: 0.059s
```

> [!NOTE]
> You can pass command line options to the test runner when using dotnet run, but you must add `--` before passing any command line options.  
> The reason for this is that the .NET SDK differentiates command line options before the `--` as command line options for 
> dotnet run itself vs. command line options after the `--` as command line options for the program.  
> Try running `dotnet run -?` and `dotnet run -- -?` to see the difference.

Excellent! Let’s go replace that sample unit test with our first real tests.
