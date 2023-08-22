# leet-code39

# Excel Sheet Column Title

Given an integer `columnNumber`, this problem requires you to return its corresponding column title as it appears in an Excel sheet.

## Problem Statement

You are given an integer `columnNumber`. Your task is to convert this column number into its corresponding column title representation, following the convention used in Excel sheets.

For example:

- A -> 1
- B -> 2
- C -> 3
- ...
- Z -> 26
- AA -> 27
- AB -> 28
- ...

### Example

**Input:**
```
columnNumber = 28
```

**Output:**
```
"AB"
```

### Constraints

- 1 <= columnNumber <= 231 - 1

## Approach

To solve this problem, you can use a mathematical approach where you convert the given column number to its corresponding column title by considering its remainder when divided by 26. Here's the general approach:

1. Initialize an empty string called `result`.
2. Loop while the `columnNumber` is greater than 0:
   - Calculate the remainder of `(columnNumber - 1) % 26`. This will give you the index of the corresponding letter (0 for 'A', 1 for 'B', and so on).
   - Add the corresponding letter to the beginning of the `result` string using `char('A' + remainder)`.
   - Update `columnNumber` as `(columnNumber - 1) / 26`.
3. Return the final `result` string.

## Implementation

Here's a sample C++ implementation of the solution:

```cpp
#include <iostream>
#include <string>

class Solution {
public:
    std::string convertToTitle(int columnNumber) {
        std::string result = "";
        
        while (columnNumber > 0) {
            int remainder = (columnNumber - 1) % 26;
            result = char('A' + remainder) + result;
            columnNumber = (columnNumber - 1) / 26;
        }
        
        return result;
    }
};

int main() {
    Solution solution;
    
    int columnNumber = 28;
    std::string columnTitle = solution.convertToTitle(columnNumber);
    
    std::cout << "Column Title for column number " << columnNumber << ": " << columnTitle << std::endl;
    
    return 0;
}
```

## Complexity Analysis

The time complexity of this solution is O(log(columnNumber)) since we are repeatedly dividing the `columnNumber` by 26 until it becomes zero. The space complexity is O(log(columnNumber)) as well due to the space required to store the resulting column title string.
