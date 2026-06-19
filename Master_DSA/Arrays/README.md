# Arrays
## 🧠 Core Intuition
The most foundational data structure. Arrays are contiguous memory blocks. The main challenge in array problems is reducing the time complexity from `O(N^2)` brute-force loops to `O(N)` single passes.

## 🛠️ Dependencies & Prerequisites
You must be completely fluent in dynamic arrays and basic traversal.

<details><summary><b>C++ Syntax & Setup</b></summary>

```cpp
#include <vector>
#include <algorithm> // for std::sort, std::reverse, std::max

int main() {
    // Initialization
    std::vector<int> arr = {1, 2, 3, 4, 5};
    std::vector<int> zeroes(10, 0); // Size 10, all 0s
    
    // Core Methods
    int size = arr.size();
    arr.push_back(6); // O(1)
    arr.pop_back();   // O(1)
    
    // Sorting & Reversing
    std::sort(arr.begin(), arr.end());
    std::reverse(arr.begin(), arr.end());
}
```
</details>

<details><summary><b>Python Syntax & Setup</b></summary>

```python
# Initialization
arr = [1, 2, 3, 4, 5]
zeroes = [0] * 10 # Size 10, all 0s

# Core Methods
n = len(arr)
arr.append(6) # O(1)
arr.pop()     # O(1)

# Sorting & Reversing
arr.sort() # In-place O(N log N)
sorted_arr = sorted(arr) # Returns new list
arr.reverse() # In-place
reversed_arr = arr[::-1] # Slicing
```
</details>

## ⏱️ Complexity Cheatsheet
| Operation | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| **Access `A[i]`** | `O(1)` | `O(1)` |
| **Search (Unsorted)** | `O(N)` | `O(1)` |
| **Insert/Delete (End)** | `O(1)` | `O(1)` |
| **Insert/Delete (Middle)** | `O(N)` | `O(1)` |

## 💡 Elite Patterns
- **Kadane's Algorithm:** Optimal `O(N)` dynamic programming approach for Maximum Subarray Sum.
- **Dutch National Flag (DNF):** Three pointers (low, mid, high) used to sort arrays of 3 unique elements (like 0s, 1s, and 2s) in a single pass.
- **Prefix Sum:** Precompute cumulative sums to answer range query sums in `O(1)` time.
- **Boyer-Moore Majority Vote:** Find the majority element (`> N/2` occurrences) in `O(N)` time and `O(1)` space.
