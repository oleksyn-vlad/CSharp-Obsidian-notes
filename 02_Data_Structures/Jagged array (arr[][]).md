Here is the note on jagged arrays.

---

## C# Jagged Arrays

A jagged array is an "array of arrays."

This is different from a 2D rectangular array (`int[,]`). With a jagged array, each "inner" array (row) can have a **different length**.

Think of it as a list of rows, where each row can be a different size.

### 1. Declaration

The syntax uses two sets of square brackets `[][]`.

C#

```C#
// Declare a jagged array (an array of int arrays)
int[][] jaggedArray;
```

### 2. Initialization

This is the most important part.

1. First, you must initialize the **outer array** (the "rows").
    
2. Then, you must initialize **each inner array** (the "columns" for that row) _individually_.
    

C#

```C#
// 1. Initialize the outer array to hold 3 inner arrays
int[][] jaggedArray = new int[3][];

// 2. Initialize each inner array with its own size
jaggedArray[0] = new int[2]; // Row 0 has 2 elements
jaggedArray[1] = new int[4]; // Row 1 has 4 elements
jaggedArray[2] = new int[3]; // Row 2 has 3 elements

// You can now assign values
jaggedArray[0][1] = 5; // [Row 0, Col 1]
jaggedArray[1][3] = 9; // [Row 1, Col 3]
```

#### Shorthand Initialization

You can also initialize it with values directly (like in C++ with `vector<vector<int>>`).

C#

```C#
// Initialize with values
string[][] teams =
{
    new string[] { "Ana", "Tom" },                // Row 0
    new string[] { "Lee", "Kim", "Chen" },      // Row 1
    new string[] { "Zac" }                       // Row 2
};
```

### 3. Accessing Elements

You access elements using `array[row][col]`.

C#

```
// Access "Kim"
Console.WriteLine(teams[1][1]); // Output: Kim
```

### 4. Iterating a Jagged Array

You must use nested loops. The key is that the inner loop must use the `Length` of the **current inner array** (`jaggedArray[row].Length`).

C#

```C#
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[] { 1, 2 };
jaggedArray[1] = new int[] { 10, 20, 30, 40 };
jaggedArray[2] = new int[] { 100 };

// Loop through the outer array (rows)
for (int row = 0; row < jaggedArray.Length; row++)
{
    // Loop through the inner array (cols for THIS row)
    // Note: jaggedArray[row].Length
    for (int col = 0; col < jaggedArray[row].Length; col++)
    {
        Console.Write(jaggedArray[row][col] + " ");
    }
    Console.WriteLine(); // Newline after each row
}
```

**Output:**

```
1 2 
10 20 30 40 
100 
```