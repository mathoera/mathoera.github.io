**Example Code**
```csharp
public class NumberChecker
{
    public bool IsEven(int number)
    {
        if (number % 2 == 0)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
}
```

**Test Methods for Branch Coverage**
```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public class NumberCheckerTests
{
    [TestMethod]
    public void IsEven_InputIsEven_ReturnsTrue()
    {
        // Arrange
        var numberChecker = new NumberChecker();
        int input = 4;

        // Act
        bool result = numberChecker.IsEven(input);

        // Assert
        Assert.IsTrue(result);
    }

    [TestMethod]
    public void IsEven_InputIsOdd_ReturnsFalse()
    {
        // Arrange
        var numberChecker = new NumberChecker();
        int input = 3;

        // Act
        bool result = numberChecker.IsEven(input);

        // Assert
        Assert.IsFalse(result);
    }
}
```
**Explanation**
- **IsEven_InputIsEven_ReturnsTrue**: This test method checks if the IsEven method returns true when the input is an even number (e.g., 4). This covers the if branch where the condition is true.
- **IsEven_InputIsOdd_ReturnsFalse**: This test method checks if the IsEven method returns false when the input is an odd number (e.g., 3). This covers the else branch where the condition is false.

By running these test methods, you ensure that both branches of the if statement (true and false) are executed at least once, achieving 100% branch coverage.
