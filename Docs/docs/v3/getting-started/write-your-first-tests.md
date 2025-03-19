# Write your first tests

Using your favorite text editor, open the UnitTest1.cs file and replace the existing test with two new ones:

```csharp
namespace MyFirstUnitTests;

public class UnitTest1
{
    [Fact]
    public void PassingTest()
    {
        Assert.Equal(4, Add(2, 2));
    }

    [Fact]
    public void FailingTest()
    {
        Assert.Equal(5, Add(2, 2));
    }

    int Add(int x, int y)
    {
        return x + y;
    }
}
```

If we run the tests again, we should see something like this:  

```shell
$ dotnet run
xUnit.net v3 In-Process Runner v1.0.0+fd19795321 (64-bit .NET 8.0.8)
  Discovering: MyFirstUnitTests
  Discovered:  MyFirstUnitTests
  Starting:    MyFirstUnitTests
    MyFirstUnitTests.UnitTest1.FailingTest [FAIL]
      Assert.Equal() Failure: Values differ
      Expected: 5
      Actual:   4
      Stack Trace:
        UnitTest1.cs(14,0): at MyFirstUnitTests.UnitTest1.FailingTest()
  Finished:    MyFirstUnitTests
=== TEST EXECUTION SUMMARY ===
   MyFirstUnitTests  Total: 2, Errors: 0, Failed: 1, Skipped: 0, Not Run: 0, Time: 0.097s
```

We can see that we have one passing test, and one failing test. That’s exactly what we would expect given what we wrote.

Now that we’re gotten our first tests to run, let’s introduce one more way to write tests: using theories.
