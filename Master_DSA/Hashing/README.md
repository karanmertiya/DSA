# Hashing & Frequency Maps
## 🧠 Core Intuition
Hashing trades space for time. By utilizing `O(N)` auxiliary space (Hash Maps or Sets), we reduce lookups, insertions, and deletions to an optimal average of `O(1)` time.

## 🛠️ Dependencies & Prerequisites
You must know how to initialize Maps/Sets, check for key existence, and iterate through Key-Value pairs.

<details><summary><b>C++ Syntax & Setup</b></summary>

```cpp
#include <unordered_map>
#include <unordered_set>

int main() {
    std::unordered_map<int, int> freq;
    std::unordered_set<int> seen;
    
    // Insertion
    freq[5] = 1;
    freq[5]++; // Auto-initializes to 0 if not present, then increments
    seen.insert(10);
    
    // Lookup
    if(freq.find(5) != freq.end()) { /* Exists */ }
    if(freq.count(5)) { /* Also checks existence */ }
    
    // Iteration
    for(auto const& [key, val] : freq) {
        // C++17 structured binding
    }
}
```
</details>

<details><summary><b>Python Syntax & Setup</b></summary>

```python
from collections import defaultdict, Counter

# Basic Dict and Set
freq = {}
seen = set()

# Safe counting (defaultdict)
freq_safe = defaultdict(int)
freq_safe[5] += 1 # No KeyError if 5 doesn't exist

# Counter (Pythonic frequency mapping)
arr = [1, 1, 2, 3]
counts = Counter(arr) # Counter({1: 2, 2: 1, 3: 1})

# Lookup and Iteration
if 5 in freq:
    pass
for key, val in freq.items():
    pass
```
</details>

## ⏱️ Complexity Cheatsheet
| Operation | Average Case | Worst Case (Collisions) |
| :--- | :--- | :--- |
| **Insert** | `O(1)` | `O(N)` |
| **Search / Lookup** | `O(1)` | `O(N)` |
| **Delete** | `O(1)` | `O(N)` |

## 💡 Elite Patterns
- **Subarray Sum Equals K:** Use a hash map to store Prefix Sum frequencies. The core formula: `Current_Sum - K = Required_Prefix`.
- **Longest Consecutive Sequence:** Insert all elements into a Hash Set. Then, only start counting a sequence if `num - 1` does NOT exist in the set.
- **Anagram Grouping:** Sort strings to use as Hash Keys, or use a 26-character frequency tuple as the key.
