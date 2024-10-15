Basis Path Testing: Ensures that all possible paths through the code are tested by identifying the set of independent paths.

### **Code Example with Basis Path Testing**
```csharp
public class ArrayProcessor
{
    public int FindMax(int[] numbers)
    {
        int max = int.MinValue; // Node 1
        for (int i = 0; i < numbers.Length; i++) // Node 2
        {
            if (numbers[i] > max) // Node 3
            {
                max = numbers[i]; // Node 4
            }
        }
        return max; // Node 5
    }
}
```

### **Test Cases for Basis Path Testing**

Basis path testing involves identifying all possible paths through the code and ensuring that each path is tested at least once. Here are the test cases:

1. **Test Case 1**:
   - **Input**: FindMax(new int[] {1, 2, 3})
   - **Expected Output**: 3
   - **Executed Paths**: 
     - Path: 1 → 2 → 3 (true) → 4 → 2 → 3 (true) → 4 → 2 → 3 (true) → 4 → 2 → 5

2. **Test Case 2**:
   - **Input**: FindMax(new int[] {-1, -2, -3})
   - **Expected Output**: -1
   - **Executed Paths**: 
     - Path: 1 → 2 → 3 (true) → 4 → 2 → 3 (false) → 2 → 3 (false) → 2 → 5

3. **Test Case 3**:
   - **Input**: FindMax(new int[] {2, 1, 3})
   - **Expected Output**: 3
   - **Executed Paths**: 
     - Path: 1 → 2 → 3 (true) → 4 → 2 → 3 (false) → 2 → 3 (true) → 4 → 2 → 5

4. **Test Case 4**:
   - **Input**: FindMax(new int[] {})
   - **Expected Output**: int.MinValue
   - **Executed Paths**: 
     - Path: 1 → 5

**Explanation**
- **Test Case 1**: Tests the scenario where the array has positive numbers in ascending order. This ensures that the loop and if condition are executed multiple times.
- **Test Case 2**: Tests the scenario where the array has negative numbers in descending order. This ensures that the loop is executed multiple times, but the if condition is false after the first iteration.
- **Test Case 3**: Tests the scenario where the array has mixed numbers. This ensures that the loop and if condition are executed in different patterns.
- **Test Case 4**: Tests the scenario where the array is empty. This ensures that the loop is not executed at all.

By running these four test cases, we ensure that all basis paths through the method are executed at least once, achieving 100% basis path coverage.

### **Test Methods**
```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public class ArrayProcessorTests
{
    [TestMethod]
    public void FindMax_InputHasPositiveNumbers_ReturnsMax()
    {
        // Arrange
        var arrayProcessor = new ArrayProcessor();
        int[] input = new int[] {1, 2, 3};

        // Act
        int result = arrayProcessor.FindMax(input);

        // Assert
        Assert.AreEqual(3, result);
    }

    [TestMethod]
    public void FindMax_InputHasNegativeNumbers_ReturnsMax()
    {
        // Arrange
        var arrayProcessor = new ArrayProcessor();
        int[] input = new int[] {-1, -2, -3};

        // Act
        int result = arrayProcessor.FindMax(input);

        // Assert
        Assert.AreEqual(-1, result);
    }

    [TestMethod]
    public void FindMax_InputHasMixedNumbers_ReturnsMax()
    {
        // Arrange
        var arrayProcessor = new ArrayProcessor();
        int[] input = new int[] {2, 1, 3};

        // Act
        int result = arrayProcessor.FindMax(input);

        // Assert
        Assert.AreEqual(3, result);
    }

    [TestMethod]
    public void FindMax_InputIsEmptyArray_ReturnsMinValue()
    {
        // Arrange
        var arrayProcessor = new ArrayProcessor();
        int[] input = new int[] {};

        // Act
        int result = arrayProcessor.FindMax(input);

        // Assert
        Assert.AreEqual(int.MinValue, result);
    }
}
```

### **Explanation**
- **FindMax_InputHasPositiveNumbers_ReturnsMax**: This test method checks if the `FindMax` method returns the maximum value when the input array has positive numbers in ascending order. This covers the path where the loop and if condition are executed multiple times.
- **FindMax_InputHasNegativeNumbers_ReturnsMax**: This test method checks if the `FindMax` method returns the maximum value when the input array has negative numbers in descending order. This covers the path where the loop is executed multiple times, but the if condition is false after the first iteration.
- **FindMax_InputHasMixedNumbers_ReturnsMax**: This test method checks if the `FindMax` method returns the maximum value when the input array has mixed numbers. This covers the path where the loop and if condition are executed in different patterns.
- **FindMax_InputIsEmptyArray_ReturnsMinValue**: This test method checks if the `FindMax` method returns `int.MinValue` when the input array is empty. This covers the path where the loop is not executed at all.

By following these test cases and methods, you can ensure that all basis paths in the `FindMax` method are covered.