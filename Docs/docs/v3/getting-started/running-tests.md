# Running tests with

# [Visual Studio](#tab/vs)

> [!NOTE]
> These screen shots were taken with Visual Studio 2022 version 17.11.0. Your screen may look slightly different if you have a newer version.

Visual Studio contains a test runner called Test Explorer that can run unit tests from a variety of third party test frameworks, including xUnit.net. The inclusion of `xunit.runner.visualstudio` (and `Microsoft.NET.Test.Sdk`) allows Test Explorer to find and run our tests.

Visual Studio works on solutions rather than projects. If your project doesn’t have a solution file yet, you can use the .NET SDK to create one. Run the following two commands from your project folder:

```shell
$ dotnet new sln
The template "Solution File" was created successfully.

$ dotnet sln add .
Project `MyFirstUnitTests.csproj` added to the solution.
```

Now open your solution with Visual Studio. Build your solution after it has opened. Make sure Test Explorer is visible (go to `Test > Test Explorer`).

## Running tests in Test Explorer

After a moment of discovery, you should see the list of discovered tests:

IMAGE

By default, the test list is arranged by project, namespace, class, and finally test method. In this case, the `MyFirstTheory` method shows 3 sub-items, as that is a data theory with 3 data rows.

Clicking the run button (the double play button) in the Test Explorer tool bar will run your tests:

IMAGE

You can double click on any test in the list to be taken directly to the source code for the test in question.

## Running tests from your source code

You should notice after the build is complete that your unit test source becomes decorated with small blue `i` icons that indicate that there is a runnable test:

IMAGE

Clicking the i will pop up a panel that will allow you to Run or Debug your tests, as well as navigate to the test inside Test Explorer. After running the tests, you’ll see that the icons now change to indicate which tests are currently passing vs. failing:

IMAGE

# [Visual Studio Code](#tab/vsc)

> [!NOTE]
> These screen shots were taken with Visual Studio Code version 1.92.2 and C# Dev Kit extension version 1.9.55. Your screen may look slightly different if you have newer versions.

To be able to build C# test projects and run their tests, install the C# Dev Kit extension into Visual Studio Code. The inclusion of `xunit.runner.visualstudio` (and `Microsoft.NET.Test.Sdk`) allows the Visual Studio Code testing panel (and the C# extension) to find and run our tests.

From the command prompt, open Visual Studio code on your project folder by running: `code` .

Using the side bar on the left, click the Explorer side bar (it’s probably already selected by default), and make sure Solution Explorer is visible. You should see something like this:

IMAGE

To build your project, right click on “MyFirstUnitTests” and choose “Build”.

## Running tests in the Testing side bar

Once the project has finished building, click on the Testing panel. After a moment of discovery, you should see the list of discovered tests:

IMAGE

By default, the test list is arranged by project, namespace, class, and finally test method. In this case, the `MyFirstTheory` method shows 3 sub-items, as that is a data theory with 3 data rows.

Clicking the run button (the double play button) in the Testing panel tool bar will run your tests:

IMAGE

You can double click on any test in the list to be taken directly to the source code for the test in question.

## Running tests from your source code

Once the project has finished building, you should notice that your unit test source becomes decorated with play icons that you can click to run your tests:

IMAGE

After running the tests, you’ll see that the icons now change to indicate which tests are currently passing vs. failing, and failed tests will include failure information inline with your source code:

IMAGE

# [JetBrains Rider](#tab/jr)

> [!NOTE]
> These screen shots were taken with Rider 2024.2. Your screen may look slightly different if you have a newer version.

Rider contains a Tests tool window that can run tests from a variety of third party test frameworks, including xUnit.net. The inclusion of `xunit.runner.visualstudio` (and `Microsoft.NET.Test.Sdk`) allows the Tests tool window to find and run our tests.

Open your project in Rider. Build the project by right clicking on it and choosing “Build Selected Projects”.

## Running tests in the Tests tool window

Once the project has finished building, click on the Tests tool window. After a moment of discovery, you should see the list of discovered tests:

IMAGE

By default, the test list is arranged by project, namespace, class, and finally test method.

Clicking the run button (the double play button) in the Tests tool window will run your tests:

IMAGE

You can double click on any test in the list to be taken directly to the source code for the test in question.

## Running tests from your source code

Once the project has finished building, you should notice that your unit test source becomes decorated with play icons that you can click to run your tests:

IMAGE

After running the tests, you’ll see that the icons now change to indicate which tests are currently passing vs. failing:

IMAGE

# [.NET Test](#tab/dnt)

In addition to directly running your test project, the inclusion of `xunit.runner.visualstudio` (and `Microsoft.NET.Test.Sdk`) means that you can also use the test runner build into the .NET SDK. It has different command line options (compare `dotnet run -- -?` with `dotnet test -?`).

The output from this runner will look different than the built-in runner:

```shell
$ dotnet test
  Determining projects to restore...
  All projects are up-to-date for restore.
  MyFirstUnitTests -> /.../MyFirstUnitTests/bin/Debug/net8.0/MyFirstUnitTests.dll
Test run for /.../MyFirstUnitTests/bin/Debug/net8.0/MyFirstUnitTests.dll (.NETCoreApp,Version=v8.0)
VSTest version 17.11.1 (x64)

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.53]     MyFirstUnitTests.UnitTest1.FailingTest [FAIL]
[xUnit.net 00:00:00.53]     MyFirstUnitTests.UnitTest1.MyFirstTheory(value: 6) [FAIL]
  Failed MyFirstUnitTests.UnitTest1.FailingTest [11 ms]
  Error Message:
   Assert.Equal() Failure: Values differ
Expected: 5
Actual:   4
  Stack Trace:
     at MyFirstUnitTests.UnitTest1.FailingTest() in /.../MyFirstUnitTests/UnitTest1.cs:line 14
  Failed MyFirstUnitTests.UnitTest1.MyFirstTheory(value: 6) [< 1 ms]
  Error Message:
   Assert.True() Failure
Expected: True
Actual:   False
  Stack Trace:
     at MyFirstUnitTests.UnitTest1.MyFirstTheory(Int32 value) in /.../MyFirstUnitTests/UnitTest1.cs:line 28

Failed!  - Failed:     2, Passed:     3, Skipped:     0, Total:     5, Duration: 35 ms - MyFirstUnitTests.dll (net8.0)
```

---
