# Basic Maths
## 🧠 Core Intuition
Mathematical concepts form the bedrock of optimal algorithms. Instead of iterating `O(N)` times to find divisors or prime numbers, mathematical tricks often reduce time complexity to `O(sqrt(N))` or even `O(1)`.

## 🛠️ Dependencies & Prerequisites
No special data structures needed, but precision and mathematical libraries are often required to prevent overflow.

<details><summary><b>C++ Syntax & Setup</b></summary>

```cpp
#include <iostream>
#include <cmath>     // For sqrt(), pow(), ceil(), floor()
#include <numeric>   // For std::gcd, std::lcm (C++17)

int main() {
    int a = 12, b = 18;
    int g = std::gcd(a, b);
    long long overflow_safe = 1LL * a * b; // Multiply with 1LL to prevent int overflow
}
```
</details>

<details><summary><b>Python Syntax & Setup</b></summary>

```python
import math

# Python handles arbitrarily large integers automatically!
a, b = 12, 18
g = math.gcd(a, b)
l = math.lcm(a, b) # Python 3.9+
sq = math.isqrt(25) # Integer square root
```
</details>

## ⏱️ Complexity Cheatsheet
| Operation | Brute Force | Optimal | Technique |
| :--- | :--- | :--- | :--- |
| **Check Prime** | `O(N)` | `O(sqrt(N))` | Check up to `sqrt(N)` |
| **Prime Factors** | `O(N)` | `O(log N)` | Sieve of Eratosthenes |
| **GCD / HCF** | `O(min(A, B))` | `O(log(min(A, B)))` | Euclidean Algorithm |
| **Trailing Zeroes** | `O(N)` | `O(log N)` | Count factors of 5 |

## 💡 Elite Patterns
- **Euclidean Algorithm:** `gcd(a, b) = gcd(b, a % b)` until `a % b == 0`.
- **Sieve of Eratosthenes:** Use a boolean array to mark non-primes up to `N` iteratively.
- **Modulo Arithmetic:** `(A * B) % M = ((A % M) * (B % M)) % M`. Used strictly to prevent integer overflow.
