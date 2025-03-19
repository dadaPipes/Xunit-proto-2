# Install the .NET SDK templates

We ship templates for creating new projects, and they must be installed before they can be used.

From your command prompt, type: dotnet new install xunit.v3.templates

You should see the output similar to this:

```shell
$ dotnet new install xunit.v3.templates
The following template packages will be installed:
   xunit.v3.templates

Success: xunit.v3.templates::1.0.0 installed the following templates:
Template Name                   Short Name        Language    Tags
------------------------------  ----------------  ----------  ----------
xUnit.net v3 Extension Project  xunit3-extension  [C#],F#,VB  Test/xUnit
xUnit.net v3 Test Project       xunit3            [C#],F#,VB  Test/xUnit
```

As of this writing, we ship two templates (xunit3 and xunit3-extension), in three languages (C#, F#, and VB.NET).
