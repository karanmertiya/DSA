# 13 Misc Revision Table

<table border="1">
  <thead>
    <tr>
      <th rowspan="2" style="width: 5%;">S.No</th>
      <th rowspan="2" style="width: 15%;">Problem Name</th>
      <th rowspan="2" style="width: 25%;">Example & Constraints</th>
      <th rowspan="2" style="width: 10%;">Complexity</th>
      <th colspan="2" style="width: 20%;">Conditions & Edge Cases</th>
      <th rowspan="2" style="width: 25%;">Logic</th>
    </tr>
    <tr>
      <th>Dependencies / Setup</th>
      <th>Edge Case Handling</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Math 01 Count Digits<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/count-digits5716/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Input: N = 12345, Output: 5</td>
      <td><b>Time:</b> O(log10 N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td><b>N=0:</b> Handled naturally if checking N > 0, otherwise special condition.</td>
      <td><b>Explanation:</b> Convert to string and return length, or repeatedly divide by 10. O(log10 N) time.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int evenlyDivides(int N){&#10;    if (N == 0) return 1;&#10;    int count = 0, temp = N;&#10;    while(temp &gt; 0) {&#10;        int digit = temp % 10;&#10;        if (digit != 0 &amp;&amp; N % digit == 0) count++;&#10;        temp /= 10;&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def evenlyDivides(N: int) -&gt; int:&#10;    if N == 0: return 1&#10;    count, temp = 0, N&#10;    while temp &gt; 0:&#10;        digit = temp % 10&#10;        if digit != 0 and N % digit == 0: count += 1&#10;        temp //= 10&#10;    return count</code></pre></details></td>
    </tr>
    <tr>
      <td>2</td>
      <td>Math 02 Reverse Integer<br><br></b> <a href='https://leetcode.com/problems/reverse-integer/' target='_blank'>LeetCode 7</a></td>
      <td><b>Example 1:</b> Input: x = 123, Output: 321</td>
      <td><b>Time:</b> O(log10 x)<br><b>Space:</b> O(1)</td>
      <td><code>#include <limits.h></code></td>
      <td><b>Overflow:</b> If ans > INT_MAX/10, return 0.</td>
      <td><b>Explanation:</b> Extract last digit using modulo, multiply answer by 10 and add. Check bounds for 32-bit integer.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int reverse(int x) {&#10;    int ans = 0;&#10;    while(x != 0) {&#10;        int digit = x % 10;&#10;        if(ans &gt; INT_MAX/10 || ans &lt; INT_MIN/10) return 0;&#10;        ans = ans * 10 + digit;&#10;        x /= 10;&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def reverse(x: int) -&gt; int:&#10;    sign = [1, -1][x &lt; 0]&#10;    ans = int(str(abs(x))[::-1])&#10;    return sign * ans if ans &lt;= 2**31 - 1 else 0</code></pre></details></td>
    </tr>
    <tr>
      <td>3</td>
      <td>Math 03 Palindrome Number<br><br></b> <a href='https://leetcode.com/problems/palindrome-number/' target='_blank'>LeetCode 9</a></td>
      <td><b>Example 1:</b> Input: x = 121, Output: true</td>
      <td><b>Time:</b> O(log10 x)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td><b>Negative Numbers:</b> Instant false. Trailing zeroes instant false.</td>
      <td><b>Explanation:</b> Negative numbers are false. Reverse half the number. If original equals reversed, it is a palindrome.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool isPalindrome(int x) {&#10;    if(x &lt; 0 || (x % 10 == 0 &amp;&amp; x != 0)) return false;&#10;    int reversedHalf = 0;&#10;    while(x &gt; reversedHalf) {&#10;        reversedHalf = reversedHalf * 10 + x % 10;&#10;        x /= 10;&#10;    }&#10;    return x == reversedHalf || x == reversedHalf / 10;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isPalindrome(x: int) -&gt; bool:&#10;    if x &lt; 0 or (x % 10 == 0 and x != 0): return False&#10;    rev = 0&#10;    while x &gt; rev:&#10;        rev = rev * 10 + x % 10&#10;        x //= 10&#10;    return x == rev or x == rev // 10</code></pre></details></td>
    </tr>
    <tr>
      <td>4</td>
      <td>Math 04 Gcd Or Hcf<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/lcm-and-gcd4551/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Input: A = 4, B = 8, Output: 4</td>
      <td><b>Time:</b> O(log(min(a,b)))<br><b>Space:</b> O(1)</td>
      <td><code>#include <numeric></code></td>
      <td><b>One is 0:</b> Return the other number.</td>
      <td><b>Explanation:</b> Euclidean Algorithm. gcd(a, b) = gcd(b, a % b). Stop when one is 0.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">long long gcd(long long a, long long b) {&#10;    while (a &gt; 0 &amp;&amp; b &gt; 0) {&#10;        if (a &gt; b) a = a % b;&#10;        else b = b % a;&#10;    }&#10;    return a == 0 ? b : a;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def gcd(a: int, b: int) -&gt; int:&#10;    while a &gt; 0 and b &gt; 0:&#10;        if a &gt; b: a = a % b&#10;        else: b = b % a&#10;    return b if a == 0 else a</code></pre></details></td>
    </tr>
    <tr>
      <td>5</td>
      <td>Math 05 Check For Prime<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/prime-number2314/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Input: N = 5, Output: 1</td>
      <td><b>Time:</b> O(sqrt(N))<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td><b>N=1:</b> Not prime.</td>
      <td><b>Explanation:</b> Check divisibility up to sqrt(N).<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int isPrime(int N){&#10;    if(N &lt;= 1) return 0;&#10;    for(int i=2; i*i&lt;=N; i++) {&#10;        if(N % i == 0) return 0;&#10;    }&#10;    return 1;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isPrime(N: int) -&gt; int:&#10;    if N &lt;= 1: return 0&#10;    for i in range(2, int(N**0.5) + 1):&#10;        if N % i == 0: return 0&#10;    return 1</code></pre></details></td>
    </tr>
    <tr>
      <td>6</td>
      <td>Math 06 Factorial Trailing Zeroes<br><br></b> <a href='https://leetcode.com/problems/factorial-trailing-zeroes/' target='_blank'>LeetCode 172</a></td>
      <td><b>Example 1:</b> Counting 5s.</td>
      <td><b>Time:</b> O(log_5(N))<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Trailing zeroes are produced by 10s, which are pairs of 2 and 5. Since 2s are more frequent, we just count the number of 5s in prime factors of numbers up to N. This is `N/5 + N/25 + N/125 + ...`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int trailingZeroes(int n) {&#10;    int count = 0;&#10;    while(n &gt; 0) {&#10;        count += n / 5;&#10;        n /= 5;&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def trailingZeroes(n: int) -&gt; int:&#10;    count = 0&#10;    while n &gt; 0:&#10;        count += n // 5&#10;        n //= 5&#10;    return count</code></pre></details></td>
    </tr>
    <tr>
      <td>7</td>
      <td>Math 07 Count Primes<br><br></b> <a href='https://leetcode.com/problems/count-primes/' target='_blank'>LeetCode 204</a></td>
      <td><b>Example 1:</b> Sieve of Eratosthenes.</td>
      <td><b>Time:</b> O(N log(log N))<br><b>Space:</b> O(N)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use the Sieve of Eratosthenes. Initialize a boolean array of size `n` with `true`. Mark `0` and `1` as `false`. For each `i` from `2` to `sqrt(n)`, if `i` is prime, mark its multiples as `false` starting from `i*i`. Finally, count the number of `true`s.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int countPrimes(int n) {&#10;    if(n &lt;= 2) return 0;&#10;    vector&lt;bool&gt; isPrime(n, true);&#10;    isPrime[0] = isPrime[1] = false;&#10;    for(int i = 2; i * i &lt; n; i++) {&#10;        if(isPrime[i]) {&#10;            for(int j = i * i; j &lt; n; j += i) {&#10;                isPrime[j] = false;&#10;            }&#10;        }&#10;    }&#10;    int count = 0;&#10;    for(int i = 2; i &lt; n; i++) {&#10;        if(isPrime[i]) count++;&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def countPrimes(n: int) -&gt; int:&#10;    if n &lt;= 2: return 0&#10;    isPrime = [True] * n&#10;    isPrime[0] = isPrime[1] = False&#10;    for i in range(2, int(n ** 0.5) + 1):&#10;        if isPrime[i]:&#10;            for j in range(i * i, n, i):&#10;                isPrime[j] = False&#10;    return sum(isPrime)</code></pre></details></td>
    </tr>
    <tr>
      <td>8</td>
      <td>Math 08 Valid Perfect Square<br><br></b> <a href='https://leetcode.com/problems/valid-perfect-square/' target='_blank'>LeetCode 367</a></td>
      <td><b>Example 1:</b> Binary Search.</td>
      <td><b>Time:</b> O(log N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use binary search from `1` to `num/2` or up to `46340` (sqrt of INT_MAX). If `mid * mid == num`, return true. Else if `mid * mid < num`, `low = mid + 1`. Else `high = mid - 1`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool isPerfectSquare(int num) {&#10;    if(num == 1) return true;&#10;    long long low = 1, high = num / 2;&#10;    while(low &lt;= high) {&#10;        long long mid = low + (high - low) / 2;&#10;        if(mid * mid == num) return true;&#10;        else if(mid * mid &lt; num) low = mid + 1;&#10;        else high = mid - 1;&#10;    }&#10;    return false;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isPerfectSquare(num: int) -&gt; bool:&#10;    if num == 1: return True&#10;    low, high = 1, num // 2&#10;    while low &lt;= high:&#10;        mid = (low + high) // 2&#10;        sq = mid * mid&#10;        if sq == num: return True&#10;        elif sq &lt; num: low = mid + 1&#10;        else: high = mid - 1&#10;    return False</code></pre></details></td>
    </tr>
    <tr>
      <td>9</td>
      <td>Math 09 Power Of Two<br><br></b> <a href='https://leetcode.com/problems/power-of-two/' target='_blank'>LeetCode 231</a></td>
      <td><b>Example 1:</b> Bit Manipulation.</td>
      <td><b>Time:</b> O(1)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> If a number is a power of two, it has exactly one bit set in its binary representation. The expression `n & (n - 1)` clears the lowest set bit. Thus, if `n > 0` and `(n & (n - 1)) == 0`, it is a power of two.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool isPowerOfTwo(int n) {&#10;    return n &gt; 0 &amp;&amp; (n &amp; (n - 1)) == 0;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isPowerOfTwo(n: int) -&gt; bool:&#10;    return n &gt; 0 and (n &amp; (n - 1)) == 0</code></pre></details></td>
    </tr>
    <tr>
      <td>10</td>
      <td>Math 10 Power Of Three<br><br></b> <a href='https://leetcode.com/problems/power-of-three/' target='_blank'>LeetCode 326</a></td>
      <td><b>Example 1:</b> Modulo with largest power.</td>
      <td><b>Time:</b> O(1)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Since `n` is a 32-bit signed integer, the largest power of 3 that fits is `3^19 = 1162261467`. A number `n` is a power of 3 if `n > 0` and `1162261467 % n == 0`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool isPowerOfThree(int n) {&#10;    return n &gt; 0 &amp;&amp; 1162261467 % n == 0;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isPowerOfThree(n: int) -&gt; bool:&#10;    return n &gt; 0 and 1162261467 % n == 0</code></pre></details></td>
    </tr>
    <tr>
      <td>11</td>
      <td>Math 11 Power Of Four<br><br></b> <a href='https://leetcode.com/problems/power-of-four/' target='_blank'>LeetCode 342</a></td>
      <td><b>Example 1:</b> Bit Manipulation.</td>
      <td><b>Time:</b> O(1)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> A power of 4 is also a power of 2, so `n > 0 && (n & (n-1)) == 0` must hold. Also, the single set bit must be at an even position (0-indexed). The mask `0x55555555` has 1s at all even positions. So `(n & 0x55555555) != 0`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool isPowerOfFour(int n) {&#10;    return n &gt; 0 &amp;&amp; (n &amp; (n - 1)) == 0 &amp;&amp; (n &amp; 0x55555555) != 0;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isPowerOfFour(n: int) -&gt; bool:&#10;    return n &gt; 0 and (n &amp; (n - 1)) == 0 and (n &amp; 0x55555555) != 0</code></pre></details></td>
    </tr>
    <tr>
      <td>12</td>
      <td>Math 12 Add Digits<br><br></b> <a href='https://leetcode.com/problems/add-digits/' target='_blank'>LeetCode 258</a></td>
      <td><b>Example 1:</b> Digital Root.</td>
      <td><b>Time:</b> O(1)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> This is known as the digital root. The formula is `1 + (n - 1) % 9`. If `n == 0`, return `0`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int addDigits(int num) {&#10;    if(num == 0) return 0;&#10;    return 1 + (num - 1) % 9;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def addDigits(num: int) -&gt; int:&#10;    if num == 0: return 0&#10;    return 1 + (num - 1) % 9</code></pre></details></td>
    </tr>
    <tr>
      <td>13</td>
      <td>Math 13 Ugly Number<br><br></b> <a href='https://leetcode.com/problems/ugly-number/' target='_blank'>LeetCode 263</a></td>
      <td><b>Example 1:</b> Division.</td>
      <td><b>Time:</b> O(log N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> If `n <= 0`, return false. Divide `n` by 2, 3, and 5 as long as it is divisible. If the remaining number is 1, it's an ugly number, else false.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool isUgly(int n) {&#10;    if(n &lt;= 0) return false;&#10;    vector&lt;int&gt; primes = {2, 3, 5};&#10;    for(int p : primes) {&#10;        while(n % p == 0) n /= p;&#10;    }&#10;    return n == 1;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def isUgly(n: int) -&gt; bool:&#10;    if n &lt;= 0: return False&#10;    for p in [2, 3, 5]:&#10;        while n % p == 0:&#10;            n //= p&#10;    return n == 1</code></pre></details></td>
    </tr>
    <tr>
      <td>14</td>
      <td>Math 14 Perfect Number<br><br></b> <a href='https://leetcode.com/problems/perfect-number/' target='_blank'>LeetCode 507</a></td>
      <td><b>Example 1:</b> Sum of divisors.</td>
      <td><b>Time:</b> O(sqrt(N))<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> If `num <= 1`, return false. Iterate up to `sqrt(num)`. If `i` divides `num`, add `i` and `num/i` to the sum. After the loop, compare sum with `num`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool checkPerfectNumber(int num) {&#10;    if(num &lt;= 1) return false;&#10;    int sum = 1;&#10;    for(int i = 2; i * i &lt;= num; i++) {&#10;        if(num % i == 0) {&#10;            sum += i;&#10;            if(i * i != num) sum += num / i;&#10;        }&#10;    }&#10;    return sum == num;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def checkPerfectNumber(num: int) -&gt; bool:&#10;    if num &lt;= 1: return False&#10;    total = 1&#10;    for i in range(2, int(num ** 0.5) + 1):&#10;        if num % i == 0:&#10;            total += i&#10;            if i * i != num: total += num // i&#10;    return total == num</code></pre></details></td>
    </tr>
    <tr>
      <td>15</td>
      <td>Math 15 Excel Sheet Column Title<br><br></b> <a href='https://leetcode.com/problems/excel-sheet-column-title/' target='_blank'>LeetCode 168</a></td>
      <td><b>Example 1:</b> Base 26 conversion.</td>
      <td><b>Time:</b> O(log_26(N))<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> This is essentially base 26 conversion, but 1-indexed (A=1, B=2, Z=26). To make it 0-indexed, decrement `columnNumber` by 1 at each step, get the remainder modulo 26, convert to character, and divide by 26.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">string convertToTitle(int columnNumber) {&#10;    string res = &quot;&quot;;&#10;    while(columnNumber &gt; 0) {&#10;        columnNumber--;&#10;        res += (char)(&#x27;A&#x27; + (columnNumber % 26));&#10;        columnNumber /= 26;&#10;    }&#10;    reverse(res.begin(), res.end());&#10;    return res;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def convertToTitle(columnNumber: int) -&gt; str:&#10;    res = []&#10;    while columnNumber &gt; 0:&#10;        columnNumber -= 1&#10;        res.append(chr(ord(&#x27;A&#x27;) + (columnNumber % 26)))&#10;        columnNumber //= 26&#10;    return &quot;&quot;.join(res[::-1])</code></pre></details></td>
    </tr>
    <tr>
      <td>16</td>
      <td>Math 16 Count Primes<br><br></b> <a href='https://leetcode.com/problems/count-primes/' target='_blank'>LeetCode 204</a></td>
      <td><b>Example 1:</b> Sieve of Eratosthenes.</td>
      <td><b>Time:</b> O(N log(log N))<br><b>Space:</b> O(N)</td>
      <td>-</td>
      <td>n <= 2</td>
      <td><b>Explanation:</b> Use the Sieve of Eratosthenes. Create a boolean array of size `n` initialized to true. Set indices 0 and 1 to false. Iterate from `p=2` to `sqrt(n)`. If `p` is prime, mark all its multiples starting from `p*p` as false. Count the remaining true values.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int countPrimes(int n) {&#10;    if(n &lt;= 2) return 0;&#10;    vector&lt;bool&gt; isPrime(n, true);&#10;    isPrime[0] = isPrime[1] = false;&#10;    for(int i = 2; i * i &lt; n; i++) {&#10;        if(isPrime[i]) {&#10;            for(int j = i * i; j &lt; n; j += i) {&#10;                isPrime[j] = false;&#10;            }&#10;        }&#10;    }&#10;    int count = 0;&#10;    for(int i = 2; i &lt; n; i++) {&#10;        if(isPrime[i]) count++;&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def countPrimes(n):&#10;    if n &lt;= 2: return 0&#10;    is_prime = [True] * n&#10;    is_prime[0] = is_prime[1] = False&#10;    for i in range(2, int(n**0.5) + 1):&#10;        if is_prime[i]:&#10;            for j in range(i*i, n, i):&#10;                is_prime[j] = False&#10;    return sum(is_prime)</code></pre></details></td>
    </tr>
    <tr>
      <td>17</td>
      <td>Math 17 Pow X N<br><br></b> <a href='https://leetcode.com/problems/powx-n/' target='_blank'>LeetCode 50</a></td>
      <td><b>Example 1:</b> Binary Exponentiation.</td>
      <td><b>Time:</b> O(log N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>Negative power, n = INT_MIN</td>
      <td><b>Explanation:</b> Use binary exponentiation. Initialize `ans = 1.0`. Keep a copy of `n` as a long long `nn`. If `nn < 0`, make it positive. While `nn > 0`, if `nn % 2 == 1`, multiply `ans` by `x` and decrement `nn`. Otherwise, square `x` and halve `nn`. If original `n < 0`, return `1.0 / ans`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">double myPow(double x, int n) {&#10;    double ans = 1.0;&#10;    long long nn = n;&#10;    if(nn &lt; 0) nn = -1 * nn;&#10;    while(nn &gt; 0) {&#10;        if(nn % 2 == 1) {&#10;            ans = ans * x;&#10;            nn = nn - 1;&#10;        } else {&#10;            x = x * x;&#10;            nn = nn / 2;&#10;        }&#10;    }&#10;    if(n &lt; 0) ans = (double)(1.0) / (double)(ans);&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def myPow(x, n):&#10;    ans, nn = 1.0, abs(n)&#10;    while nn &gt; 0:&#10;        if nn % 2 == 1:&#10;            ans *= x&#10;            nn -= 1&#10;        else:&#10;            x *= x&#10;            nn //= 2&#10;    return ans if n &gt;= 0 else 1.0 / ans</code></pre></details></td>
    </tr>
    <tr>
      <td>18</td>
      <td>Math 18 Sieve Of Eratosthenes<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/sieve-of-eratosthenes5242/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Classic implementation.</td>
      <td><b>Time:</b> O(N log(log N))<br><b>Space:</b> O(N)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Same as `countPrimes`, but return the actual prime numbers in a list instead of just the count.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; sieveOfEratosthenes(int N) {&#10;    vector&lt;int&gt; primes;&#10;    vector&lt;bool&gt; isPrime(N + 1, true);&#10;    isPrime[0] = isPrime[1] = false;&#10;    for(int i = 2; i * i &lt;= N; i++) {&#10;        if(isPrime[i]) {&#10;            for(int j = i * i; j &lt;= N; j += i) {&#10;                isPrime[j] = false;&#10;            }&#10;        }&#10;    }&#10;    for(int i = 2; i &lt;= N; i++) {&#10;        if(isPrime[i]) primes.push_back(i);&#10;    }&#10;    return primes;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def sieveOfEratosthenes(N):&#10;    is_prime = [True] * (N + 1)&#10;    is_prime[0] = is_prime[1] = False&#10;    for i in range(2, int(N**0.5) + 1):&#10;        if is_prime[i]:&#10;            for j in range(i*i, N + 1, i):&#10;                is_prime[j] = False&#10;    return [i for i in range(2, N + 1) if is_prime[i]]</code></pre></details></td>
    </tr>
    <tr>
      <td>19</td>
      <td>Math 19 Factorial Trailing Zeroes<br><br></b> <a href='https://leetcode.com/problems/factorial-trailing-zeroes/' target='_blank'>LeetCode 172</a></td>
      <td><b>Example 1:</b> Count 5s.</td>
      <td><b>Time:</b> O(log5(N))<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Trailing zeroes are produced by the prime factors 2 and 5. Since 2 is always more abundant than 5, we just need to count the number of 5s in the prime factorization of `n!`. This is done by repeatedly dividing `n` by 5 and adding the quotients.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int trailingZeroes(int n) {&#10;    int count = 0;&#10;    while(n &gt; 0) {&#10;        count += n / 5;&#10;        n /= 5;&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def trailingZeroes(n):&#10;    count = 0&#10;    while n &gt; 0:&#10;        count += n // 5&#10;        n //= 5&#10;    return count</code></pre></details></td>
    </tr>
    <tr>
      <td>20</td>
      <td>Hash 20 Count Frequencies<br><br></b> <a href='https://www.geeksforgeeks.org/problems/frequency-of-array-elements-1587115620/1' target='_blank'>GeeksforGeeks</a></td>
      <td><b>Example 1:</b> Input: arr = [10, 5, 10, 15, 10, 5], Output: 10->3, 5->2, 15->1<br><br><b>Note (Constraint):</b> 1 &le; N &le; 10<sup>5</sup></td>
      <td><b>Time:</b> O(N<sup>2</sup>) (Trade-off)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td>-</td>
      <td><b>Marking Checked:</b> Requires mutating array or extra boolean array to track checked elements.</td>
      <td><b>Explanation:</b> Use two nested loops to count occurrences. Mark visited elements to avoid recounting.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;iostream&gt;&#10;&#10;void countFreqBrute(std::vector&lt;int&gt;&amp; arr) {&#10;    std::vector&lt;bool&gt; visited(arr.size(), false);&#10;    for(int i=0; i&lt;arr.size(); i++) {&#10;        if(visited[i]) continue;&#10;        int count = 1;&#10;        for(int j=i+1; j&lt;arr.size(); j++) {&#10;            if(arr[i] == arr[j]) {&#10;                visited[j] = true;&#10;                count++;&#10;            }&#10;        }&#10;    }&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def count_freq_brute(arr: list[int]) -&gt; None:&#10;    visited = [False] * len(arr)&#10;    for i in range(len(arr)):&#10;        if visited[i]: continue&#10;        count = 1&#10;        for j in range(i+1, len(arr)):&#10;            if arr[i] == arr[j]:&#10;                visited[j] = True&#10;                count += 1</code></pre></details></td>
    </tr>
    <tr>
      <td>21</td>
      <td>Hash 21 Highest Lowest Frequency<br><br></b> <a href='https://leetcode.com/problems/sort-array-by-increasing-frequency/' target='_blank'>LeetCode 1636</a></td>
      <td><b>Example 1:</b> Input: arr = [10, 5, 10, 15, 10, 5], Output: Highest=10, Lowest=15<br><br><b>Note (Constraint):</b> 1 &le; N &le; 10<sup>5</sup></td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>std::unordered_map</code></td>
      <td><b>Initialization:</b> Set min_freq to `INT_MAX` properly to allow map values to overwrite it.</td>
      <td><b>Explanation:</b> Build a frequency map, then iterate through the map to find the max and min frequencies.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_map&gt;&#10;#include &lt;climits&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;void findHighLowFreq(std::vector&lt;int&gt;&amp; arr) {&#10;    std::unordered_map&lt;int, int&gt; freq;&#10;    for(int num : arr) freq[num]++;&#10;    &#10;    int max_f = 0, min_f = INT_MAX;&#10;    int max_ele = 0, min_ele = 0;&#10;    &#10;    for(auto it : freq) {&#10;        if(it.second &gt; max_f) { max_f = it.second; max_ele = it.first; }&#10;        if(it.second &lt; min_f) { min_f = it.second; min_ele = it.first; }&#10;    }&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def find_high_low_freq(arr: list[int]) -&gt; tuple:&#10;    freq = {}&#10;    for num in arr:&#10;        freq[num] = freq.get(num, 0) + 1&#10;    &#10;    max_f, min_f = 0, float(&#x27;inf&#x27;)&#10;    max_ele, min_ele = 0, 0&#10;    &#10;    for ele, count in freq.items():&#10;        if count &gt; max_f:&#10;            max_f, max_ele = count, ele&#10;        if count &lt; min_f:&#10;            min_f, min_ele = count, ele&#10;    return max_ele, min_ele</code></pre></details></td>
    </tr>
    <tr>
      <td>22</td>
      <td>Hash 22 Intersection Of Two Arrays<br><br></b> <a href='https://leetcode.com/problems/intersection-of-two-arrays/' target='_blank'>LeetCode 349</a></td>
      <td><b>Example 1:</b> Input: nums1 = [1,2,2,1], nums2 = [2,2], Output: [2]<br><br><b>Note (Constraint):</b> 1 &le; N, M &le; 1000</td>
      <td><b>Time:</b> O(N + M) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>std::unordered_set</code> / <code>set()</code></td>
      <td><b>Duplicate Match Prevention:</b> Erase matched elements from the set immediately to prevent duplicate intersections.</td>
      <td><b>Explanation:</b> Store elements of the first array in a Hash Set, then iterate over the second array to find matches.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_set&gt;&#10;&#10;std::vector&lt;int&gt; intersection(std::vector&lt;int&gt;&amp; nums1, std::vector&lt;int&gt;&amp; nums2) {&#10;    std::unordered_set&lt;int&gt; s(nums1.begin(), nums1.end());&#10;    std::vector&lt;int&gt; res;&#10;    for(int num : nums2) {&#10;        if(s.find(num) != s.end()) {&#10;            res.push_back(num);&#10;            s.erase(num); // Ensure uniqueness&#10;        }&#10;    }&#10;    return res;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def intersection(nums1: list[int], nums2: list[int]) -&gt; list[int]:&#10;    set1 = set(nums1)&#10;    res = []&#10;    for num in nums2:&#10;        if num in set1:&#10;            res.append(num)&#10;            set1.remove(num) # Ensure uniqueness&#10;    return res</code></pre></details></td>
    </tr>
    <tr>
      <td>23</td>
      <td>Hash 23 Union Of Two Arrays<br><br></b> <a href='https://www.geeksforgeeks.org/problems/union-of-two-arrays3538/1' target='_blank'>GeeksforGeeks</a></td>
      <td><b>Example 1:</b> Input: a = [1, 2, 3], b = [2, 3, 4], Output: [1, 2, 3, 4]<br><br><b>Note (Constraint):</b> Arrays may not be sorted.</td>
      <td><b>Time:</b> O(N + M) (Constraint)<br><b>Space:</b> O(N + M) (Trade-off)</td>
      <td><code>std::unordered_set</code> / <code>set()</code></td>
      <td><b>Unordered Limitation:</b> If the problem expects sorted union, `std::set` must be used increasing time to `O((N+M)log(N+M))`.</td>
      <td><b>Explanation:</b> Insert all elements from both arrays into a Hash Set. The Set natively drops duplicates.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_set&gt;&#10;&#10;std::vector&lt;int&gt; findUnion(std::vector&lt;int&gt;&amp; a, std::vector&lt;int&gt;&amp; b) {&#10;    std::unordered_set&lt;int&gt; s;&#10;    for(int num : a) s.insert(num);&#10;    for(int num : b) s.insert(num);&#10;    &#10;    std::vector&lt;int&gt; res(s.begin(), s.end());&#10;    return res;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def find_union(a: list[int], b: list[int]) -&gt; list[int]:&#10;    # Set union operator implicitly merges and drops duplicates&#10;    s = set(a) | set(b)&#10;    return list(s)</code></pre></details></td>
    </tr>
    <tr>
      <td>24</td>
      <td>Hash 24 Subarray With 0 Sum<br><br></b> <a href='https://www.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/1' target='_blank'>GeeksforGeeks</a></td>
      <td><b>Example 1:</b> Input: arr = [4, 2, -3, 1, 6], Output: true (2, -3, 1)<br><br><b>Note (Constraint):</b> Array contains positive and negative integers.</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>std::unordered_set</code></td>
      <td><b>Zero Prefix Edge Case:</b> If `sum == 0` during traversal, the subarray naturally started from index 0.</td>
      <td><b>Explanation:</b> Use a Prefix Sum and a Hash Set. If a prefix sum repeats, or equals 0, a 0-sum subarray exists between the identical prefix sums.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_set&gt;&#10;&#10;bool hasZeroSumSubarray(std::vector&lt;int&gt;&amp; arr) {&#10;    std::unordered_set&lt;int&gt; prefix_sums;&#10;    int sum = 0;&#10;    for(int num : arr) {&#10;        sum += num;&#10;        if(sum == 0 || prefix_sums.find(sum) != prefix_sums.end()) {&#10;            return true;&#10;        }&#10;        prefix_sums.insert(sum);&#10;    }&#10;    return false;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def has_zero_sum_subarray(arr: list[int]) -&gt; bool:&#10;    prefix_sums = set()&#10;    curr_sum = 0&#10;    for num in arr:&#10;        curr_sum += num&#10;        if curr_sum == 0 or curr_sum in prefix_sums:&#10;            return True&#10;        prefix_sums.add(curr_sum)&#10;    return False</code></pre></details></td>
    </tr>
    <tr>
      <td>25</td>
      <td>Hash 25 Subarray Sum Equals K<br><br></b> <a href='https://leetcode.com/problems/subarray-sum-equals-k/' target='_blank'>LeetCode 560</a></td>
      <td><b>Example 1:</b> Input: nums = [1,1,1], k = 2, Output: 2<br><br><b>Note (Constraint):</b> Negative numbers allowed, preventing pure Sliding Window approaches.</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>std::unordered_map</code></td>
      <td><b>Base Case Injection:</b> Must initialize map with `(0, 1)` to correctly count subarrays starting natively from index 0.</td>
      <td><b>Explanation:</b> Maintain a Hash Map of `prefix_sum` -> `frequency`. If `curr_sum - k` exists in the map, add its frequency to the count.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_map&gt;&#10;&#10;int subarraySum(std::vector&lt;int&gt;&amp; nums, int k) {&#10;    std::unordered_map&lt;int, int&gt; prefix_freq;&#10;    prefix_freq[0] = 1; // Base case for subarrays starting at index 0&#10;    &#10;    int count = 0, sum = 0;&#10;    for(int num : nums) {&#10;        sum += num;&#10;        int remove = sum - k;&#10;        if(prefix_freq.find(remove) != prefix_freq.end()) {&#10;            count += prefix_freq[remove];&#10;        }&#10;        prefix_freq[sum]++;&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def subarray_sum(nums: list[int], k: int) -&gt; int:&#10;    prefix_freq = {0: 1}&#10;    count = 0&#10;    curr_sum = 0&#10;    for num in nums:&#10;        curr_sum += num&#10;        remove = curr_sum - k&#10;        if remove in prefix_freq:&#10;            count += prefix_freq[remove]&#10;        prefix_freq[curr_sum] = prefix_freq.get(curr_sum, 0) + 1&#10;    return count</code></pre></details></td>
    </tr>
    <tr>
      <td>26</td>
      <td>Hash 26 Longest Subarray With 0 Sum<br><br></b> <a href='https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1' target='_blank'>GeeksforGeeks</a></td>
      <td><b>Example 1:</b> Input: arr = [15,-2,2,-8,1,7,10,23], Output: 5<br><br><b>Note (Constraint):</b> 1 &le; N &le; 10<sup>5</sup></td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>std::unordered_map</code></td>
      <td><b>Longest Policy:</b> We only insert `sum` into the map if it doesn't exist to preserve the earliest index and maximize distance.</td>
      <td><b>Explanation:</b> Store `prefix_sum` -> `index` in Hash Map. If sum repeats, calculate distance `i - hash[sum]`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_map&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;int maxLen(std::vector&lt;int&gt;&amp; arr) {&#10;    std::unordered_map&lt;int, int&gt; prefix_index;&#10;    int max_len = 0, sum = 0;&#10;    for(int i = 0; i &lt; arr.size(); i++) {&#10;        sum += arr[i];&#10;        if(sum == 0) {&#10;            max_len = i + 1;&#10;        } else if(prefix_index.find(sum) != prefix_index.end()) {&#10;            max_len = std::max(max_len, i - prefix_index[sum]);&#10;        } else {&#10;            prefix_index[sum] = i; // Store only first occurrence&#10;        }&#10;    }&#10;    return max_len;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def max_len(arr: list[int]) -&gt; int:&#10;    prefix_index = {}&#10;    max_len = sum = 0&#10;    for i, num in enumerate(arr):&#10;        sum += num&#10;        if sum == 0:&#10;            max_len = i + 1&#10;        elif sum in prefix_index:&#10;            max_len = max(max_len, i - prefix_index[sum])&#10;        else:&#10;            prefix_index[sum] = i&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>27</td>
      <td>Hash 27 Longest Subarray With Sum K<br><br></b> <a href='https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1' target='_blank'>GeeksforGeeks</a></td>
      <td><b>Example 1:</b> Input: arr = [10, 5, 2, 7, 1, 9], k = 15, Output: 4<br><br><b>Note (Constraint):</b> 1 &le; N &le; 10<sup>5</sup></td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>std::unordered_map</code></td>
      <td><b>Zero Elements Rule:</b> Never overwrite existing prefix sums in the map, otherwise arrays with zero elements will shorten the max length.</td>
      <td><b>Explanation:</b> Prefix Sum Map storing indices. Check if `sum - K` exists in map and calculate index difference.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_map&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;int lenOfLongSubarr(std::vector&lt;int&gt;&amp; arr, int k) {&#10;    std::unordered_map&lt;long long, int&gt; prefix_index;&#10;    int max_len = 0;&#10;    long long sum = 0;&#10;    for(int i = 0; i &lt; arr.size(); i++) {&#10;        sum += arr[i];&#10;        if(sum == k) {&#10;            max_len = i + 1;&#10;        }&#10;        long long needed = sum - k;&#10;        if(prefix_index.find(needed) != prefix_index.end()) {&#10;            max_len = std::max(max_len, i - prefix_index[needed]);&#10;        }&#10;        if(prefix_index.find(sum) == prefix_index.end()) {&#10;            prefix_index[sum] = i;&#10;        }&#10;    }&#10;    return max_len;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def len_of_long_subarr(arr: list[int], k: int) -&gt; int:&#10;    prefix_index = {}&#10;    max_len = sum = 0&#10;    for i, num in enumerate(arr):&#10;        sum += num&#10;        if sum == k:&#10;            max_len = i + 1&#10;        needed = sum - k&#10;        if needed in prefix_index:&#10;            max_len = max(max_len, i - prefix_index[needed])&#10;        if sum not in prefix_index:&#10;            prefix_index[sum] = i&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>28</td>
      <td>Hash 28 Two Sum<br><br></b> <a href='https://leetcode.com/problems/two-sum/' target='_blank'>LeetCode 1</a></td>
      <td><b>Example 1:</b> Input: nums = [2,7,11,15], target = 9, Output: [0,1]</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td><code>std::unordered_map</code></td>
      <td><b>Duplicate Elements:</b> Storing elements as we iterate safely handles duplicates (e.g., target 6, array [3,3]).</td>
      <td><b>Explanation:</b> Iterate while storing numbers and their indices in a hash map. Check if `target - num` already exists.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_map&gt;&#10;std::vector&lt;int&gt; twoSum(std::vector&lt;int&gt;&amp; nums, int target) {&#10;    std::unordered_map&lt;int, int&gt; mpp;&#10;    for(int i = 0; i &lt; nums.size(); i++) {&#10;        int needed = target - nums[i];&#10;        if(mpp.find(needed) != mpp.end()) {&#10;            return {mpp[needed], i};&#10;        }&#10;        mpp[nums[i]] = i;&#10;    }&#10;    return {};&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def twoSum(nums: list[int], target: int) -&gt; list[int]:&#10;    mpp = {}&#10;    for i, num in enumerate(nums):&#10;        needed = target - num&#10;        if needed in mpp:&#10;            return [mpp[needed], i]&#10;        mpp[num] = i&#10;    return []</code></pre></details></td>
    </tr>
    <tr>
      <td>29</td>
      <td>Hash 29 Group Anagrams<br><br></b> <a href='https://leetcode.com/problems/group-anagrams/' target='_blank'>LeetCode 49</a></td>
      <td><b>Example 1:</b> Input: strs = ["eat","tea","tan","ate","nat","bat"], Output: [["bat"],["nat","tan"],["ate","eat","tea"]]</td>
      <td><b>Time:</b> O(N * K log K)<br><b>Space:</b> O(N * K)</td>
      <td><code>std::unordered_map</code>, <code>std::sort</code></td>
      <td><b>Empty Strings:</b> Safely handled since an empty string sorted is still empty, forming a valid key.</td>
      <td><b>Explanation:</b> Use a hash map where the key is the sorted version of the string, and the value is a list of anagrams.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;string&gt;&#10;#include &lt;unordered_map&gt;&#10;#include &lt;algorithm&gt;&#10;std::vector&lt;std::vector&lt;std::string&gt;&gt; groupAnagrams(std::vector&lt;std::string&gt;&amp; strs) {&#10;    std::unordered_map&lt;std::string, std::vector&lt;std::string&gt;&gt; mpp;&#10;    for(std::string s : strs) {&#10;        std::string key = s;&#10;        std::sort(key.begin(), key.end());&#10;        mpp[key].push_back(s);&#10;    }&#10;    std::vector&lt;std::vector&lt;std::string&gt;&gt; ans;&#10;    for(auto it : mpp) {&#10;        ans.push_back(it.second);&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">from collections import defaultdict&#10;def groupAnagrams(strs: list[str]) -&gt; list[list[str]]:&#10;    mpp = defaultdict(list)&#10;    for s in strs:&#10;        mpp[tuple(sorted(s))].append(s)&#10;    return list(mpp.values())</code></pre></details></td>
    </tr>
    <tr>
      <td>30</td>
      <td>Hash 30 Longest Consecutive Sequence<br><br></b> <a href='https://leetcode.com/problems/longest-consecutive-sequence/' target='_blank'>LeetCode 128</a></td>
      <td><b>Example 1:</b> Input: nums = [100,4,200,1,3,2], Output: 4 (The sequence is [1, 2, 3, 4])</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N)</td>
      <td><code>std::unordered_set</code></td>
      <td><b>Duplicate Elements:</b> Handled automatically by the Set.</td>
      <td><b>Explanation:</b> Insert all elements into a Hash Set. Iterate through elements. If `num - 1` is NOT in the set, it's the start of a sequence. Count forwards.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;unordered_set&gt;&#10;#include &lt;algorithm&gt;&#10;int longestConsecutive(std::vector&lt;int&gt;&amp; nums) {&#10;    std::unordered_set&lt;int&gt; st(nums.begin(), nums.end());&#10;    int max_len = 0;&#10;    for(int num : st) {&#10;        if(st.find(num - 1) == st.end()) {&#10;            int curr_num = num;&#10;            int curr_len = 1;&#10;            while(st.find(curr_num + 1) != st.end()) {&#10;                curr_num++;&#10;                curr_len++;&#10;            }&#10;            max_len = std::max(max_len, curr_len);&#10;        }&#10;    }&#10;    return max_len;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def longestConsecutive(nums: list[int]) -&gt; int:&#10;    num_set = set(nums)&#10;    max_len = 0&#10;    for num in num_set:&#10;        if num - 1 not in num_set:&#10;            curr_num = num&#10;            curr_len = 1&#10;            while curr_num + 1 in num_set:&#10;                curr_num += 1&#10;                curr_len += 1&#10;            max_len = max(max_len, curr_len)&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>31</td>
      <td>Hash 31 Subarray With 0 Sum<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Hash Set.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td>Hash Set</td>
      <td>-</td>
      <td><b>Explanation:</b> Maintain the prefix sum. If the current prefix sum is 0, or if it has been seen before (stored in a Hash Set), then a subarray with 0 sum exists.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool subArrayExists(int arr[], int n) {&#10;    unordered_set&lt;int&gt; s;&#10;    int sum = 0;&#10;    for(int i = 0; i &lt; n; i++) {&#10;        sum += arr[i];&#10;        if(sum == 0 || s.find(sum) != s.end()) return true;&#10;        s.insert(sum);&#10;    }&#10;    return false;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def subArrayExists(arr, n):&#10;    s = set()&#10;    sum_val = 0&#10;    for num in arr:&#10;        sum_val += num&#10;        if sum_val == 0 or sum_val in s: return True&#10;        s.add(sum_val)&#10;    return False</code></pre></details></td>
    </tr>
    <tr>
      <td>32</td>
      <td>Hash 32 Longest Subarray With 0 Sum<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Hash Map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> Maintain the prefix sum and a hash map storing the first occurrence index of each prefix sum. If sum is 0, length is `i+1`. If sum is in the map, length is `i - map[sum]`. Update max length.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int maxLen(vector&lt;int&gt;&amp; A, int n) {&#10;    unordered_map&lt;int, int&gt; m;&#10;    int maxi = 0, sum = 0;&#10;    for(int i = 0; i &lt; n; i++) {&#10;        sum += A[i];&#10;        if(sum == 0) maxi = i + 1;&#10;        else {&#10;            if(m.find(sum) != m.end()) {&#10;                maxi = max(maxi, i - m[sum]);&#10;            } else {&#10;                m[sum] = i;&#10;            }&#10;        }&#10;    }&#10;    return maxi;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def maxLen(n, arr):&#10;    m = {}&#10;    maxi, sum_val = 0, 0&#10;    for i in range(n):&#10;        sum_val += arr[i]&#10;        if sum_val == 0: maxi = i + 1&#10;        else:&#10;            if sum_val in m:&#10;                maxi = max(maxi, i - m[sum_val])&#10;            else:&#10;                m[sum_val] = i&#10;    return maxi</code></pre></details></td>
    </tr>
    <tr>
      <td>33</td>
      <td>Hash 33 Two Sum<br><br></b> <a href='https://leetcode.com/problems/two-sum/' target='_blank'>LeetCode 1</a></td>
      <td><b>Example 1:</b> Hash Map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a hash map to store `value -> index`. Iterate through array, check if `target - nums[i]` exists in map. If yes, return current index and mapped index. Else, store current value and index.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; twoSum(vector&lt;int&gt;&amp; nums, int target) {&#10;    unordered_map&lt;int, int&gt; m;&#10;    for(int i = 0; i &lt; nums.size(); i++) {&#10;        if(m.find(target - nums[i]) != m.end()) {&#10;            return {m[target - nums[i]], i};&#10;        }&#10;        m[nums[i]] = i;&#10;    }&#10;    return {};&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def twoSum(nums, target):&#10;    m = {}&#10;    for i, num in enumerate(nums):&#10;        if target - num in m:&#10;            return [m[target - num], i]&#10;        m[num] = i&#10;    return []</code></pre></details></td>
    </tr>
    <tr>
      <td>34</td>
      <td>Hash 34 Longest Consecutive Sequence<br><br></b> <a href='https://leetcode.com/problems/longest-consecutive-sequence/' target='_blank'>LeetCode 128</a></td>
      <td><b>Example 1:</b> Hash Set.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td>Hash Set</td>
      <td>-</td>
      <td><b>Explanation:</b> Insert all elements into a hash set. Iterate through the set. If `x - 1` is not in the set, `x` is the start of a sequence. Count consecutive elements `x + 1`, `x + 2`... Update max length.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int longestConsecutive(vector&lt;int&gt;&amp; nums) {&#10;    unordered_set&lt;int&gt; s(nums.begin(), nums.end());&#10;    int maxLen = 0;&#10;    for(int num : s) {&#10;        if(s.find(num - 1) == s.end()) {&#10;            int currNum = num;&#10;            int currLen = 1;&#10;            while(s.find(currNum + 1) != s.end()) {&#10;                currNum++;&#10;                currLen++;&#10;            }&#10;            maxLen = max(maxLen, currLen);&#10;        }&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def longestConsecutive(nums):&#10;    s = set(nums)&#10;    max_len = 0&#10;    for num in s:&#10;        if num - 1 not in s:&#10;            curr_num, curr_len = num, 1&#10;            while curr_num + 1 in s:&#10;                curr_num += 1&#10;                curr_len += 1&#10;            max_len = max(max_len, curr_len)&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>35</td>
      <td>Hash 35 Sort Characters By Frequency<br><br></b> <a href='https://leetcode.com/problems/sort-characters-by-frequency/' target='_blank'>LeetCode 451</a></td>
      <td><b>Example 1:</b> Hash Map + Priority Queue / Sorting.</td>
      <td><b>Time:</b> O(N log K) where K is unique chars<br><b>Space:</b> O(K)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> Count frequencies using a hash map. Add pairs `(freq, char)` to a max heap or vector and sort. Reconstruct string.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">string frequencySort(string s) {&#10;    unordered_map&lt;char, int&gt; freq;&#10;    for(char c : s) freq[c]++;&#10;    vector&lt;pair&lt;int, char&gt;&gt; v;&#10;    for(auto it : freq) v.push_back({it.second, it.first});&#10;    sort(v.rbegin(), v.rend());&#10;    string ans = &quot;&quot;;&#10;    for(auto it : v) {&#10;        ans += string(it.first, it.second);&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">from collections import Counter&#10;def frequencySort(s):&#10;    counts = Counter(s)&#10;    return &quot;&quot;.join(char * count for char, count in counts.most_common())</code></pre></details></td>
    </tr>
    <tr>
      <td>36</td>
      <td>Hash 36 Group Anagrams<br><br></b> <a href='https://leetcode.com/problems/group-anagrams/' target='_blank'>LeetCode 49</a></td>
      <td><b>Example 1:</b> Hash Map with sorted string as key.</td>
      <td><b>Time:</b> O(N * K log K) where K is max string length<br><b>Space:</b> O(N * K)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a hash map. The key is the sorted version of the string (or a character count string), and the value is a list of original strings that match this key.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;vector&lt;string&gt;&gt; groupAnagrams(vector&lt;string&gt;&amp; strs) {&#10;    unordered_map&lt;string, vector&lt;string&gt;&gt; m;&#10;    for(string s : strs) {&#10;        string key = s;&#10;        sort(key.begin(), key.end());&#10;        m[key].push_back(s);&#10;    }&#10;    vector&lt;vector&lt;string&gt;&gt; ans;&#10;    for(auto it : m) ans.push_back(it.second);&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">from collections import defaultdict&#10;def groupAnagrams(strs):&#10;    m = defaultdict(list)&#10;    for s in strs:&#10;        m[tuple(sorted(s))].append(s)&#10;    return list(m.values())</code></pre></details></td>
    </tr>
    <tr>
      <td>37</td>
      <td>Hash 37 Count Distinct Elements In Every Window<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/count-distinct-elements-in-every-window/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Sliding Window + Hash Map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a hash map to keep track of element frequencies in the window of size K. The number of distinct elements is the size of the hash map. As window slides, increment frequency of new element, decrement frequency of outgoing element. If frequency becomes 0, remove it from map.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; countDistinct(int A[], int n, int k) {&#10;    unordered_map&lt;int, int&gt; m;&#10;    vector&lt;int&gt; ans;&#10;    for(int i = 0; i &lt; k; i++) m[A[i]]++;&#10;    ans.push_back(m.size());&#10;    for(int i = k; i &lt; n; i++) {&#10;        m[A[i - k]]--;&#10;        if(m[A[i - k]] == 0) m.erase(A[i - k]);&#10;        m[A[i]]++;&#10;        ans.push_back(m.size());&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def countDistinct(arr, n, k):&#10;    m = {}&#10;    ans = []&#10;    for i in range(k):&#10;        m[arr[i]] = m.get(arr[i], 0) + 1&#10;    ans.append(len(m))&#10;    for i in range(k, n):&#10;        m[arr[i - k]] -= 1&#10;        if m[arr[i - k]] == 0: del m[arr[i - k]]&#10;        m[arr[i]] = m.get(arr[i], 0) + 1&#10;        ans.append(len(m))&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>38</td>
      <td>Hash 38 Design Hashset<br><br></b> <a href='https://leetcode.com/problems/design-hashset/' target='_blank'>LeetCode 705</a></td>
      <td><b>Example 1:</b> Array of Linked Lists (Chaining).</td>
      <td><b>Time:</b> O(1) average, O(N) worst case<br><b>Space:</b> O(N)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a large array (e.g., size 10000) of linked lists or vectors. The hash function maps `key` to `key % 10000`. To add, if not present in the bucket, append it. To remove, find and erase. To contain, iterate through bucket.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">class MyHashSet {&#10;    vector&lt;list&lt;int&gt;&gt; buckets;&#10;    int size = 10000;&#10;public:&#10;    MyHashSet() {&#10;        buckets.resize(size);&#10;    }&#10;    void add(int key) {&#10;        int i = key % size;&#10;        auto it = find(buckets[i].begin(), buckets[i].end(), key);&#10;        if(it == buckets[i].end()) buckets[i].push_back(key);&#10;    }&#10;    void remove(int key) {&#10;        int i = key % size;&#10;        auto it = find(buckets[i].begin(), buckets[i].end(), key);&#10;        if(it != buckets[i].end()) buckets[i].erase(it);&#10;    }&#10;    bool contains(int key) {&#10;        int i = key % size;&#10;        auto it = find(buckets[i].begin(), buckets[i].end(), key);&#10;        return it != buckets[i].end();&#10;    }&#10;};</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">class MyHashSet:&#10;    def __init__(self):&#10;        self.size = 10000&#10;        self.buckets = [[] for _ in range(self.size)]&#10;    def add(self, key: int) -&gt; None:&#10;        i = key % self.size&#10;        if key not in self.buckets[i]:&#10;            self.buckets[i].append(key)&#10;    def remove(self, key: int) -&gt; None:&#10;        i = key % self.size&#10;        if key in self.buckets[i]:&#10;            self.buckets[i].remove(key)&#10;    def contains(self, key: int) -&gt; bool:&#10;        return key in self.buckets[key % self.size]</code></pre></details></td>
    </tr>
    <tr>
      <td>39</td>
      <td>Sw 39 Trapping Rain Water<br><br></b> <a href='https://leetcode.com/problems/trapping-rain-water/' target='_blank'>LeetCode 42</a></td>
      <td><b>Example 1:</b> Input: height = [0,1,0,2,1,0,1,3,2,1,2,1], Output: 6</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td><b>Local Maxima:</b> Water trapped at `i` relies on the absolute minimum of the highest bars to its left and right.</td>
      <td><b>Explanation:</b> Two pointers `left` and `right`. Maintain `left_max` and `right_max`. Move the pointer pointing to the smaller max, adding trapped water.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;algorithm&gt;&#10;int trap(std::vector&lt;int&gt;&amp; height) {&#10;    int n = height.size();&#10;    int left = 0, right = n - 1;&#10;    int res = 0, maxLeft = 0, maxRight = 0;&#10;    while (left &lt;= right) {&#10;        if (height[left] &lt;= height[right]) {&#10;            if (height[left] &gt;= maxLeft) maxLeft = height[left];&#10;            else res += maxLeft - height[left];&#10;            left++;&#10;        } else {&#10;            if (height[right] &gt;= maxRight) maxRight = height[right];&#10;            else res += maxRight - height[right];&#10;            right--;&#10;        }&#10;    }&#10;    return res;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def trap(height: list[int]) -&gt; int:&#10;    left, right = 0, len(height) - 1&#10;    res, maxLeft, maxRight = 0, 0, 0&#10;    while left &lt;= right:&#10;        if height[left] &lt;= height[right]:&#10;            if height[left] &gt;= maxLeft: maxLeft = height[left]&#10;            else: res += maxLeft - height[left]&#10;            left += 1&#10;        else:&#10;            if height[right] &gt;= maxRight: maxRight = height[right]&#10;            else: res += maxRight - height[right]&#10;            right -= 1&#10;    return res</code></pre></details></td>
    </tr>
    <tr>
      <td>40</td>
      <td>Sw 40 Count Occurrences Of Anagrams<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Fixed window and frequency map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(26) = O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Maintain a frequency map of the pattern. Use a sliding window of size equal to the length of the pattern. Keep track of the number of characters fully matched (`count`). If `count` equals the number of unique characters in the pattern, an anagram is found.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int search(string pat, string txt) {&#10;    int k = pat.length(), n = txt.length();&#10;    if(k &gt; n) return 0;&#10;    vector&lt;int&gt; count(26, 0);&#10;    for(char c : pat) count[c - &#x27;a&#x27;]++;&#10;    int i = 0, j = 0, ans = 0;&#10;    int distinct = 0;&#10;    for(int x : count) if(x &gt; 0) distinct++;&#10;    while(j &lt; n) {&#10;        count[txt[j] - &#x27;a&#x27;]--;&#10;        if(count[txt[j] - &#x27;a&#x27;] == 0) distinct--;&#10;        if(j - i + 1 &lt; k) j++;&#10;        else if(j - i + 1 == k) {&#10;            if(distinct == 0) ans++;&#10;            count[txt[i] - &#x27;a&#x27;]++;&#10;            if(count[txt[i] - &#x27;a&#x27;] == 1) distinct++;&#10;            i++; j++;&#10;        }&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def search(pat: str, txt: str) -&gt; int:&#10;    k, n = len(pat), len(txt)&#10;    if k &gt; n: return 0&#10;    count = collections.Counter(pat)&#10;    distinct = len(count)&#10;    i = j = ans = 0&#10;    while j &lt; n:&#10;        if txt[j] in count:&#10;            count[txt[j]] -= 1&#10;            if count[txt[j]] == 0:&#10;                distinct -= 1&#10;        if j - i + 1 &lt; k:&#10;            j += 1&#10;        elif j - i + 1 == k:&#10;            if distinct == 0:&#10;                ans += 1&#10;            if txt[i] in count:&#10;                count[txt[i]] += 1&#10;                if count[txt[i]] == 1:&#10;                    distinct += 1&#10;            i += 1&#10;            j += 1&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>41</td>
      <td>Sw 41 Maximum Of All Subarrays Of Size K<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Deque.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td><code>#include <deque></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Use a deque to store indices of elements. The deque will maintain elements in decreasing order. For each element, remove elements from the back of the deque that are smaller than the current element. Also, remove elements from the front that are out of the current window. The front of the deque will always have the maximum element of the current window.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector &lt;int&gt; max_of_subarrays(int *arr, int n, int k) {&#10;    vector&lt;int&gt; res;&#10;    deque&lt;int&gt; dq;&#10;    for(int i = 0; i &lt; n; i++) {&#10;        if(!dq.empty() &amp;&amp; dq.front() == i - k) dq.pop_front();&#10;        while(!dq.empty() &amp;&amp; arr[dq.back()] &lt;= arr[i]) dq.pop_back();&#10;        dq.push_back(i);&#10;        if(i &gt;= k - 1) res.push_back(arr[dq.front()]);&#10;    }&#10;    return res;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def max_of_subarrays(arr: List[int], n: int, k: int) -&gt; List[int]:&#10;    res = []&#10;    dq = collections.deque()&#10;    for i in range(n):&#10;        if dq and dq[0] == i - k:&#10;            dq.popleft()&#10;        while dq and arr[dq[-1]] &lt;= arr[i]:&#10;            dq.pop()&#10;        dq.append(i)&#10;        if i &gt;= k - 1:&#10;            res.append(arr[dq[0]])&#10;    return res</code></pre></details></td>
    </tr>
    <tr>
      <td>42</td>
      <td>Sw 42 Longest Subarray With Sum K<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Prefix sum with hash map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td><code>#include <unordered_map></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Keep track of the prefix sum. Store the first occurrence of each prefix sum in a hash map. If `prefix_sum - K` exists in the hash map, calculate the length of the subarray and update the maximum length.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int lenOfLongSubarr(int A[],  int N, int K) {&#10;    unordered_map&lt;int, int&gt; preSum;&#10;    int sum = 0, maxLen = 0;&#10;    for(int i = 0; i &lt; N; i++) {&#10;        sum += A[i];&#10;        if(sum == K) maxLen = max(maxLen, i + 1);&#10;        if(preSum.find(sum - K) != preSum.end()) {&#10;            maxLen = max(maxLen, i - preSum[sum - K]);&#10;        }&#10;        if(preSum.find(sum) == preSum.end()) {&#10;            preSum[sum] = i;&#10;        }&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def lenOfLongSubarr(A: List[int], N: int, K: int) -&gt; int:&#10;    preSum = {}&#10;    currSum = 0&#10;    maxLen = 0&#10;    for i in range(N):&#10;        currSum += A[i]&#10;        if currSum == K:&#10;            maxLen = max(maxLen, i + 1)&#10;        if currSum - K in preSum:&#10;            maxLen = max(maxLen, i - preSum[currSum - K])&#10;        if currSum not in preSum:&#10;            preSum[currSum] = i&#10;    return maxLen</code></pre></details></td>
    </tr>
    <tr>
      <td>43</td>
      <td>Sw 43 Longest Substring Without Repeating Characters<br><br></b> <a href='https://leetcode.com/problems/longest-substring-without-repeating-characters/' target='_blank'>LeetCode 3</a></td>
      <td><b>Example 1:</b> Sliding window with hash set/map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td><code>#include <unordered_set></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window. Keep expanding the window by adding characters. If a duplicate character is found, shrink the window from the left until the duplicate is removed.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int lengthOfLongestSubstring(string s) {&#10;    unordered_set&lt;char&gt; seen;&#10;    int l = 0, r = 0, maxLen = 0;&#10;    while(r &lt; s.length()) {&#10;        if(seen.find(s[r]) == seen.end()) {&#10;            seen.insert(s[r]);&#10;            maxLen = max(maxLen, r - l + 1);&#10;            r++;&#10;        } else {&#10;            seen.erase(s[l]);&#10;            l++;&#10;        }&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def lengthOfLongestSubstring(s: str) -&gt; int:&#10;    seen = set()&#10;    l = 0&#10;    maxLen = 0&#10;    for r in range(len(s)):&#10;        while s[r] in seen:&#10;            seen.remove(s[l])&#10;            l += 1&#10;        seen.add(s[r])&#10;        maxLen = max(maxLen, r - l + 1)&#10;    return maxLen</code></pre></details></td>
    </tr>
    <tr>
      <td>44</td>
      <td>Sw 44 Minimum Window Substring<br><br></b> <a href='https://leetcode.com/problems/minimum-window-substring/' target='_blank'>LeetCode 76</a></td>
      <td><b>Example 1:</b> Variable sliding window.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td><code>#include <unordered_map></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Maintain a frequency map of `t`. Expand the window by moving `right`. When the window contains all characters of `t`, try to shrink it by moving `left` to find the minimum window. Keep track of the minimum window length and its starting index.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">string minWindow(string s, string t) {&#10;    if(s.length() &lt; t.length()) return &quot;&quot;;&#10;    vector&lt;int&gt; count(128, 0);&#10;    for(char c : t) count[c]++;&#10;    int l = 0, r = 0, minLen = INT_MAX, minStart = 0, required = t.length();&#10;    while(r &lt; s.length()) {&#10;        if(count[s[r]] &gt; 0) required--;&#10;        count[s[r]]--;&#10;        r++;&#10;        while(required == 0) {&#10;            if(r - l &lt; minLen) {&#10;                minLen = r - l;&#10;                minStart = l;&#10;            }&#10;            count[s[l]]++;&#10;            if(count[s[l]] &gt; 0) required++;&#10;            l++;&#10;        }&#10;    }&#10;    return minLen == INT_MAX ? &quot;&quot; : s.substr(minStart, minLen);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def minWindow(s: str, t: str) -&gt; str:&#10;    if len(s) &lt; len(t): return &quot;&quot;&#10;    count = collections.Counter(t)&#10;    required = len(t)&#10;    l = r = 0&#10;    minLen = float(&#x27;inf&#x27;)&#10;    minStart = 0&#10;    while r &lt; len(s):&#10;        if count[s[r]] &gt; 0:&#10;            required -= 1&#10;        count[s[r]] -= 1&#10;        r += 1&#10;        while required == 0:&#10;            if r - l &lt; minLen:&#10;                minLen = r - l&#10;                minStart = l&#10;            count[s[l]] += 1&#10;            if count[s[l]] &gt; 0:&#10;                required += 1&#10;            l += 1&#10;    return &quot;&quot; if minLen == float(&#x27;inf&#x27;) else s[minStart:minStart+minLen]</code></pre></details></td>
    </tr>
    <tr>
      <td>45</td>
      <td>Sw 45 Sliding Window Maximum<br><br></b> <a href='https://leetcode.com/problems/sliding-window-maximum/' target='_blank'>LeetCode 239</a></td>
      <td><b>Example 1:</b> Deque.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td><code>#include <deque></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Use a deque to store indices. The deque maintains elements in decreasing order. Remove elements from the back if they are smaller than the current element. Remove elements from the front if they are out of the window. The front element is the maximum of the current window.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; maxSlidingWindow(vector&lt;int&gt;&amp; nums, int k) {&#10;    vector&lt;int&gt; res;&#10;    deque&lt;int&gt; dq;&#10;    for(int i = 0; i &lt; nums.size(); i++) {&#10;        if(!dq.empty() &amp;&amp; dq.front() == i - k) dq.pop_front();&#10;        while(!dq.empty() &amp;&amp; nums[dq.back()] &lt;= nums[i]) dq.pop_back();&#10;        dq.push_back(i);&#10;        if(i &gt;= k - 1) res.push_back(nums[dq.front()]);&#10;    }&#10;    return res;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def maxSlidingWindow(nums: List[int], k: int) -&gt; List[int]:&#10;    res = []&#10;    dq = collections.deque()&#10;    for i in range(len(nums)):&#10;        if dq and dq[0] == i - k:&#10;            dq.popleft()&#10;        while dq and nums[dq[-1]] &lt;= nums[i]:&#10;            dq.pop()&#10;        dq.append(i)&#10;        if i &gt;= k - 1:&#10;            res.append(nums[dq[0]])&#10;    return res</code></pre></details></td>
    </tr>
    <tr>
      <td>46</td>
      <td>Sw 46 Longest K Unique Characters Substring<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Variable window and hash map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td><code>#include <unordered_map></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Maintain a hash map of character frequencies. Expand the window by moving `j`. If the number of unique characters exceeds `k`, shrink the window from the left (`i`) until the number of unique characters is `k`. Update the maximum length when exactly `k` unique characters are present.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int longestKSubstr(string s, int k) {&#10;    unordered_map&lt;char, int&gt; count;&#10;    int i = 0, j = 0, maxLen = -1;&#10;    while(j &lt; s.length()) {&#10;        count[s[j]]++;&#10;        if(count.size() == k) maxLen = max(maxLen, j - i + 1);&#10;        else if(count.size() &gt; k) {&#10;            while(count.size() &gt; k) {&#10;                count[s[i]]--;&#10;                if(count[s[i]] == 0) count.erase(s[i]);&#10;                i++;&#10;            }&#10;        }&#10;        j++;&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def longestKSubstr(s: str, k: int) -&gt; int:&#10;    count = collections.defaultdict(int)&#10;    i = j = 0&#10;    maxLen = -1&#10;    while j &lt; len(s):&#10;        count[s[j]] += 1&#10;        if len(count) == k:&#10;            maxLen = max(maxLen, j - i + 1)&#10;        elif len(count) &gt; k:&#10;            while len(count) &gt; k:&#10;                count[s[i]] -= 1&#10;                if count[s[i]] == 0:&#10;                    del count[s[i]]&#10;                i += 1&#10;        j += 1&#10;    return maxLen</code></pre></details></td>
    </tr>
    <tr>
      <td>47</td>
      <td>Sw 47 Subarrays With K Different Integers<br><br></b> <a href='https://leetcode.com/problems/subarrays-with-k-different-integers/' target='_blank'>LeetCode 992</a></td>
      <td><b>Example 1:</b> Exact K = atMost(K) - atMost(K-1).</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td><code>#include <unordered_map></code></td>
      <td>-</td>
      <td><b>Explanation:</b> Finding exact `k` distinct is hard directly. Instead, find subarrays with at most `k` distinct integers. The number of exact `k` is `atMost(k) - atMost(k - 1)`. The `atMost` function uses a sliding window.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int atMost(vector&lt;int&gt;&amp; nums, int k) {&#10;    unordered_map&lt;int, int&gt; count;&#10;    int res = 0, i = 0;&#10;    for(int j = 0; j &lt; nums.size(); j++) {&#10;        if(count[nums[j]] == 0) k--;&#10;        count[nums[j]]++;&#10;        while(k &lt; 0) {&#10;            count[nums[i]]--;&#10;            if(count[nums[i]] == 0) k++;&#10;            i++;&#10;        }&#10;        res += j - i + 1;&#10;    }&#10;    return res;&#10;}&#10;int subarraysWithKDistinct(vector&lt;int&gt;&amp; nums, int k) {&#10;    return atMost(nums, k) - atMost(nums, k - 1);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def subarraysWithKDistinct(nums: List[int], k: int) -&gt; int:&#10;    def atMost(k):&#10;        count = collections.defaultdict(int)&#10;        res = i = 0&#10;        for j in range(len(nums)):&#10;            if count[nums[j]] == 0: k -= 1&#10;            count[nums[j]] += 1&#10;            while k &lt; 0:&#10;                count[nums[i]] -= 1&#10;                if count[nums[i]] == 0: k += 1&#10;                i += 1&#10;            res += j - i + 1&#10;        return res&#10;    return atMost(k) - atMost(k - 1)</code></pre></details></td>
    </tr>
    <tr>
      <td>48</td>
      <td>Sw 48 Minimum Size Subarray Sum<br><br></b> <a href='https://leetcode.com/problems/minimum-size-subarray-sum/' target='_blank'>LeetCode 209</a></td>
      <td><b>Example 1:</b> Variable sliding window.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window. Add elements to the current sum. While the sum is >= target, update the minimum length and shrink the window from the left.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int minSubArrayLen(int target, vector&lt;int&gt;&amp; nums) {&#10;    int l = 0, sum = 0, minLen = INT_MAX;&#10;    for(int r = 0; r &lt; nums.size(); r++) {&#10;        sum += nums[r];&#10;        while(sum &gt;= target) {&#10;            minLen = min(minLen, r - l + 1);&#10;            sum -= nums[l++];&#10;        }&#10;    }&#10;    return minLen == INT_MAX ? 0 : minLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def minSubArrayLen(target: int, nums: List[int]) -&gt; int:&#10;    l = sum = 0&#10;    minLen = float(&#x27;inf&#x27;)&#10;    for r in range(len(nums)):&#10;        sum += nums[r]&#10;        while sum &gt;= target:&#10;            minLen = min(minLen, r - l + 1)&#10;            sum -= nums[l]&#10;            l += 1&#10;    return 0 if minLen == float(&#x27;inf&#x27;) else minLen</code></pre></details></td>
    </tr>
    <tr>
      <td>49</td>
      <td>Sw 49 Fruits Into Baskets<br><br></b> <a href='https://leetcode.com/problems/fruit-into-baskets/' target='_blank'>LeetCode 904</a></td>
      <td><b>Example 1:</b> Longest subarray with at most 2 distinct elements.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1) (at most 3 elements in map)</td>
      <td><code>#include <unordered_map></code></td>
      <td>-</td>
      <td><b>Explanation:</b> This translates to finding the longest subarray with at most 2 distinct elements. Maintain a frequency map and use a sliding window. If distinct elements > 2, shrink the window until distinct elements <= 2.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int totalFruit(vector&lt;int&gt;&amp; fruits) {&#10;    unordered_map&lt;int, int&gt; count;&#10;    int l = 0, maxFruits = 0;&#10;    for(int r = 0; r &lt; fruits.size(); r++) {&#10;        count[fruits[r]]++;&#10;        while(count.size() &gt; 2) {&#10;            count[fruits[l]]--;&#10;            if(count[fruits[l]] == 0) count.erase(fruits[l]);&#10;            l++;&#10;        }&#10;        maxFruits = max(maxFruits, r - l + 1);&#10;    }&#10;    return maxFruits;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">import collections&#10;def totalFruit(fruits: List[int]) -&gt; int:&#10;    count = collections.defaultdict(int)&#10;    l = maxFruits = 0&#10;    for r in range(len(fruits)):&#10;        count[fruits[r]] += 1&#10;        while len(count) &gt; 2:&#10;            count[fruits[l]] -= 1&#10;            if count[fruits[l]] == 0:&#10;                del count[fruits[l]]&#10;            l += 1&#10;        maxFruits = max(maxFruits, r - l + 1)&#10;    return maxFruits</code></pre></details></td>
    </tr>
    <tr>
      <td>50</td>
      <td>Sw 50 Max Consecutive Ones Iii<br><br></b> <a href='https://leetcode.com/problems/max-consecutive-ones-iii/' target='_blank'>LeetCode 1004</a></td>
      <td><b>Example 1:</b> Sliding Window.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window. Expand the right pointer. If the element is 0, increment a zero counter. While the zero counter > k, shrink the window from the left by moving the left pointer and decrementing the zero counter if left element is 0. The max window size is the answer.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int longestOnes(vector&lt;int&gt;&amp; nums, int k) {&#10;    int left = 0, right = 0, zeroes = 0, maxLen = 0;&#10;    while(right &lt; nums.size()) {&#10;        if(nums[right] == 0) zeroes++;&#10;        while(zeroes &gt; k) {&#10;            if(nums[left] == 0) zeroes--;&#10;            left++;&#10;        }&#10;        maxLen = max(maxLen, right - left + 1);&#10;        right++;&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def longestOnes(nums, k):&#10;    left = 0&#10;    zeroes = 0&#10;    max_len = 0&#10;    for right in range(len(nums)):&#10;        if nums[right] == 0: zeroes += 1&#10;        while zeroes &gt; k:&#10;            if nums[left] == 0: zeroes -= 1&#10;            left += 1&#10;        max_len = max(max_len, right - left + 1)&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>51</td>
      <td>Sw 51 Fruit Into Baskets<br><br></b> <a href='https://leetcode.com/problems/fruit-into-baskets/' target='_blank'>LeetCode 904</a></td>
      <td><b>Example 1:</b> Longest Subarray with at most 2 distinct elements.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> This translates to finding the longest subarray with at most 2 distinct elements. Use a hash map to keep track of fruit counts in the current window. Expand right, update map. If map size > 2, shrink from left until map size is 2.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int totalFruit(vector&lt;int&gt;&amp; fruits) {&#10;    unordered_map&lt;int, int&gt; count;&#10;    int left = 0, maxLen = 0;&#10;    for(int right = 0; right &lt; fruits.size(); right++) {&#10;        count[fruits[right]]++;&#10;        while(count.size() &gt; 2) {&#10;            count[fruits[left]]--;&#10;            if(count[fruits[left]] == 0) count.erase(fruits[left]);&#10;            left++;&#10;        }&#10;        maxLen = max(maxLen, right - left + 1);&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def totalFruit(fruits):&#10;    count = {}&#10;    left = 0&#10;    max_len = 0&#10;    for right in range(len(fruits)):&#10;        count[fruits[right]] = count.get(fruits[right], 0) + 1&#10;        while len(count) &gt; 2:&#10;            count[fruits[left]] -= 1&#10;            if count[fruits[left]] == 0: del count[fruits[left]]&#10;            left += 1&#10;        max_len = max(max_len, right - left + 1)&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>52</td>
      <td>Sw 52 Longest Repeating Character Replacement<br><br></b> <a href='https://leetcode.com/problems/longest-repeating-character-replacement/' target='_blank'>LeetCode 424</a></td>
      <td><b>Example 1:</b> Sliding Window + Max Freq.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window. Maintain the character frequencies and the `max_freq` in the window. The number of replacements needed is `window_size - max_freq`. If this is > k, shrink the window from left and decrement the corresponding frequency.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int characterReplacement(string s, int k) {&#10;    vector&lt;int&gt; count(26, 0);&#10;    int left = 0, maxFreq = 0, maxLen = 0;&#10;    for(int right = 0; right &lt; s.length(); right++) {&#10;        count[s[right] - &#x27;A&#x27;]++;&#10;        maxFreq = max(maxFreq, count[s[right] - &#x27;A&#x27;]);&#10;        if((right - left + 1) - maxFreq &gt; k) {&#10;            count[s[left] - &#x27;A&#x27;]--;&#10;            left++;&#10;        }&#10;        maxLen = max(maxLen, right - left + 1);&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def characterReplacement(s, k):&#10;    count = [0] * 26&#10;    left = 0&#10;    max_freq = 0&#10;    max_len = 0&#10;    for right in range(len(s)):&#10;        count[ord(s[right]) - ord(&#x27;A&#x27;)] += 1&#10;        max_freq = max(max_freq, count[ord(s[right]) - ord(&#x27;A&#x27;)])&#10;        if (right - left + 1) - max_freq &gt; k:&#10;            count[ord(s[left]) - ord(&#x27;A&#x27;)] -= 1&#10;            left += 1&#10;        max_len = max(max_len, right - left + 1)&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>53</td>
      <td>Sw 53 Binary Subarrays With Sum<br><br></b> <a href='https://leetcode.com/problems/binary-subarrays-with-sum/' target='_blank'>LeetCode 930</a></td>
      <td><b>Example 1:</b> atMost(goal) - atMost(goal - 1).</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use the helper function `atMost(goal)` which finds the number of subarrays with sum <= goal. The answer is `atMost(goal) - atMost(goal - 1)`. In `atMost`, use a sliding window to maintain the sum.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int atMost(vector&lt;int&gt;&amp; nums, int goal) {&#10;    if(goal &lt; 0) return 0;&#10;    int left = 0, sum = 0, count = 0;&#10;    for(int right = 0; right &lt; nums.size(); right++) {&#10;        sum += nums[right];&#10;        while(sum &gt; goal) {&#10;            sum -= nums[left++];&#10;        }&#10;        count += (right - left + 1);&#10;    }&#10;    return count;&#10;}&#10;int numSubarraysWithSum(vector&lt;int&gt;&amp; nums, int goal) {&#10;    return atMost(nums, goal) - atMost(nums, goal - 1);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def numSubarraysWithSum(nums, goal):&#10;    def atMost(k):&#10;        if k &lt; 0: return 0&#10;        left, sum_val, count = 0, 0, 0&#10;        for right in range(len(nums)):&#10;            sum_val += nums[right]&#10;            while sum_val &gt; k:&#10;                sum_val -= nums[left]&#10;                left += 1&#10;            count += (right - left + 1)&#10;        return count&#10;    return atMost(goal) - atMost(goal - 1)</code></pre></details></td>
    </tr>
    <tr>
      <td>54</td>
      <td>Sw 54 Count Number Of Nice Subarrays<br><br></b> <a href='https://leetcode.com/problems/count-number-of-nice-subarrays/' target='_blank'>LeetCode 1248</a></td>
      <td><b>Example 1:</b> atMost(k) - atMost(k - 1).</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Replace all odd numbers with 1 and even numbers with 0. The problem then reduces to finding the number of subarrays with a sum equal to k. Use the `atMost(k) - atMost(k - 1)` sliding window approach.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int atMost(vector&lt;int&gt;&amp; nums, int k) {&#10;    if(k &lt; 0) return 0;&#10;    int left = 0, count = 0, res = 0;&#10;    for(int right = 0; right &lt; nums.size(); right++) {&#10;        if(nums[right] % 2 != 0) count++;&#10;        while(count &gt; k) {&#10;            if(nums[left] % 2 != 0) count--;&#10;            left++;&#10;        }&#10;        res += (right - left + 1);&#10;    }&#10;    return res;&#10;}&#10;int numberOfSubarrays(vector&lt;int&gt;&amp; nums, int k) {&#10;    return atMost(nums, k) - atMost(nums, k - 1);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def numberOfSubarrays(nums, k):&#10;    def atMost(limit):&#10;        if limit &lt; 0: return 0&#10;        left, count, res = 0, 0, 0&#10;        for right in range(len(nums)):&#10;            if nums[right] % 2 != 0: count += 1&#10;            while count &gt; limit:&#10;                if nums[left] % 2 != 0: count -= 1&#10;                left += 1&#10;            res += (right - left + 1)&#10;        return res&#10;    return atMost(k) - atMost(k - 1)</code></pre></details></td>
    </tr>
    <tr>
      <td>55</td>
      <td>Sw 55 Number Of Substrings Containing All Three Characters<br><br></b> <a href='https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/' target='_blank'>LeetCode 1358</a></td>
      <td><b>Example 1:</b> Store last seen indices.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Iterate through the string. Track the last seen indices of 'a', 'b', and 'c'. If all three have been seen, the number of valid substrings ending at the current index `i` is `1 + min(last_a, last_b, last_c)`. Add this to the total count.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int numberOfSubstrings(string s) {&#10;    int last[3] = {-1, -1, -1};&#10;    int count = 0;&#10;    for(int i = 0; i &lt; s.length(); i++) {&#10;        last[s[i] - &#x27;a&#x27;] = i;&#10;        if(last[0] != -1 &amp;&amp; last[1] != -1 &amp;&amp; last[2] != -1) {&#10;            count += (1 + min({last[0], last[1], last[2]}));&#10;        }&#10;    }&#10;    return count;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def numberOfSubstrings(s):&#10;    last = [-1, -1, -1]&#10;    count = 0&#10;    for i in range(len(s)):&#10;        last[ord(s[i]) - ord(&#x27;a&#x27;)] = i&#10;        if last[0] != -1 and last[1] != -1 and last[2] != -1:&#10;            count += 1 + min(last)&#10;    return count</code></pre></details></td>
    </tr>
    <tr>
      <td>56</td>
      <td>Sw 56 Maximum Points You Can Obtain From Cards<br><br></b> <a href='https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/' target='_blank'>LeetCode 1423</a></td>
      <td><b>Example 1:</b> Sliding Window on remaining cards.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Instead of picking cards from the ends, find the subarray of length `N - K` that has the minimum sum. Subtract this minimum sum from the total sum of the array. That gives the maximum score.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int maxScore(vector&lt;int&gt;&amp; cardPoints, int k) {&#10;    int n = cardPoints.size();&#10;    int totalSum = 0, windowSum = 0;&#10;    for(int i = 0; i &lt; n; i++) {&#10;        totalSum += cardPoints[i];&#10;        if(i &lt; n - k) windowSum += cardPoints[i];&#10;    }&#10;    int minWindowSum = windowSum;&#10;    for(int i = n - k; i &lt; n; i++) {&#10;        windowSum += cardPoints[i] - cardPoints[i - (n - k)];&#10;        minWindowSum = min(minWindowSum, windowSum);&#10;    }&#10;    return totalSum - minWindowSum;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def maxScore(cardPoints, k):&#10;    n = len(cardPoints)&#10;    total_sum = sum(cardPoints)&#10;    window_size = n - k&#10;    window_sum = sum(cardPoints[:window_size])&#10;    min_window_sum = window_sum&#10;    for i in range(window_size, n):&#10;        window_sum += cardPoints[i] - cardPoints[i - window_size]&#10;        min_window_sum = min(min_window_sum, window_sum)&#10;    return total_sum - min_window_sum</code></pre></details></td>
    </tr>
    <tr>
      <td>57</td>
      <td>Sw 57 Subarrays With K Different Integers<br><br></b> <a href='https://leetcode.com/problems/subarrays-with-k-different-integers/' target='_blank'>LeetCode 992</a></td>
      <td><b>Example 1:</b> atMost(k) - atMost(k - 1).</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(N)</td>
      <td>Hash Map</td>
      <td>-</td>
      <td><b>Explanation:</b> Like "Binary Subarrays With Sum", the number of subarrays with exactly k distinct integers is `atMost(k) - atMost(k-1)`. The `atMost` function uses a sliding window with a hash map to track the frequencies of elements.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int atMost(vector&lt;int&gt;&amp; nums, int k) {&#10;    if(k == 0) return 0;&#10;    unordered_map&lt;int, int&gt; count;&#10;    int left = 0, res = 0;&#10;    for(int right = 0; right &lt; nums.size(); right++) {&#10;        count[nums[right]]++;&#10;        while(count.size() &gt; k) {&#10;            count[nums[left]]--;&#10;            if(count[nums[left]] == 0) count.erase(nums[left]);&#10;            left++;&#10;        }&#10;        res += (right - left + 1);&#10;    }&#10;    return res;&#10;}&#10;int subarraysWithKDistinct(vector&lt;int&gt;&amp; nums, int k) {&#10;    return atMost(nums, k) - atMost(nums, k - 1);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def subarraysWithKDistinct(nums, k):&#10;    def atMost(limit):&#10;        if limit == 0: return 0&#10;        count = {}&#10;        left, res = 0, 0&#10;        for right in range(len(nums)):&#10;            count[nums[right]] = count.get(nums[right], 0) + 1&#10;            while len(count) &gt; limit:&#10;                count[nums[left]] -= 1&#10;                if count[nums[left]] == 0: del count[nums[left]]&#10;                left += 1&#10;            res += (right - left + 1)&#10;        return res&#10;    return atMost(k) - atMost(k - 1)</code></pre></details></td>
    </tr>
    <tr>
      <td>58</td>
      <td>Sw 58 Minimum Window Substring<br><br></b> <a href='https://leetcode.com/problems/minimum-window-substring/' target='_blank'>LeetCode 76</a></td>
      <td><b>Example 1:</b> Hash map + Sliding Window.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>t > s length</td>
      <td><b>Explanation:</b> Store frequency of chars in `t`. Use `left` and `right` pointers. Expand `right`, if the character is in `t`, decrease its required count. If all characters are found, update the minimum length and start shrinking from `left`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">string minWindow(string s, string t) {&#10;    vector&lt;int&gt; count(128, 0);&#10;    for(char c : t) count[c]++;&#10;    int required = t.length();&#10;    int left = 0, minLen = INT_MAX, minStart = 0;&#10;    for(int right = 0; right &lt; s.length(); right++) {&#10;        if(count[s[right]] &gt; 0) required--;&#10;        count[s[right]]--;&#10;        while(required == 0) {&#10;            if(right - left + 1 &lt; minLen) {&#10;                minLen = right - left + 1;&#10;                minStart = left;&#10;            }&#10;            count[s[left]]++;&#10;            if(count[s[left]] &gt; 0) required++;&#10;            left++;&#10;        }&#10;    }&#10;    return minLen == INT_MAX ? &quot;&quot; : s.substr(minStart, minLen);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def minWindow(s, t):&#10;    count = [0] * 128&#10;    for c in t: count[ord(c)] += 1&#10;    required = len(t)&#10;    left, min_len, min_start = 0, float(&#x27;inf&#x27;), 0&#10;    for right in range(len(s)):&#10;        if count[ord(s[right])] &gt; 0: required -= 1&#10;        count[ord(s[right])] -= 1&#10;        while required == 0:&#10;            if right - left + 1 &lt; min_len:&#10;                min_len = right - left + 1&#10;                min_start = left&#10;            count[ord(s[left])] += 1&#10;            if count[ord(s[left])] &gt; 0: required += 1&#10;            left += 1&#10;    return &quot;&quot; if min_len == float(&#x27;inf&#x27;) else s[min_start:min_start + min_len]</code></pre></details></td>
    </tr>
    <tr>
      <td>59</td>
      <td>Sw 59 Find All Anagrams In A String<br><br></b> <a href='https://leetcode.com/problems/find-all-anagrams-in-a-string/' target='_blank'>LeetCode 438</a></td>
      <td><b>Example 1:</b> Fixed Window + Hash Map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Create frequency arrays for `p` and a window of size `p.length()` in `s`. Slide the window across `s`, updating the window frequencies. If the arrays match, add the window's start index to the result.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; findAnagrams(string s, string p) {&#10;    vector&lt;int&gt; ans;&#10;    if(p.length() &gt; s.length()) return ans;&#10;    vector&lt;int&gt; countP(26, 0), countS(26, 0);&#10;    for(int i = 0; i &lt; p.length(); i++) {&#10;        countP[p[i] - &#x27;a&#x27;]++;&#10;        countS[s[i] - &#x27;a&#x27;]++;&#10;    }&#10;    if(countP == countS) ans.push_back(0);&#10;    for(int i = p.length(); i &lt; s.length(); i++) {&#10;        countS[s[i] - &#x27;a&#x27;]++;&#10;        countS[s[i - p.length()] - &#x27;a&#x27;]--;&#10;        if(countP == countS) ans.push_back(i - p.length() + 1);&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def findAnagrams(s, p):&#10;    ans = []&#10;    if len(p) &gt; len(s): return ans&#10;    countP, countS = [0]*26, [0]*26&#10;    for i in range(len(p)):&#10;        countP[ord(p[i]) - ord(&#x27;a&#x27;)] += 1&#10;        countS[ord(s[i]) - ord(&#x27;a&#x27;)] += 1&#10;    if countP == countS: ans.append(0)&#10;    for i in range(len(p), len(s)):&#10;        countS[ord(s[i]) - ord(&#x27;a&#x27;)] += 1&#10;        countS[ord(s[i - len(p)]) - ord(&#x27;a&#x27;)] -= 1&#10;        if countP == countS: ans.append(i - len(p) + 1)&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>60</td>
      <td>Sw 60 Longest K Unique Characters Substring<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Sliding Window + Hash Map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window `[left, right]` and a hash map to count characters. If map size > K, shrink window from `left` until map size == K. If map size == K, update max length.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int longestKSubstr(string s, int k) {&#10;    unordered_map&lt;char, int&gt; m;&#10;    int left = 0, right = 0, maxLen = -1;&#10;    while(right &lt; s.length()) {&#10;        m[s[right]]++;&#10;        if(m.size() == k) maxLen = max(maxLen, right - left + 1);&#10;        else if(m.size() &gt; k) {&#10;            while(m.size() &gt; k) {&#10;                m[s[left]]--;&#10;                if(m[s[left]] == 0) m.erase(s[left]);&#10;                left++;&#10;            }&#10;        }&#10;        right++;&#10;    }&#10;    return maxLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def longestKSubstr(s, k):&#10;    m = {}&#10;    left, max_len = 0, -1&#10;    for right in range(len(s)):&#10;        m[s[right]] = m.get(s[right], 0) + 1&#10;        if len(m) == k: max_len = max(max_len, right - left + 1)&#10;        elif len(m) &gt; k:&#10;            while len(m) &gt; k:&#10;                m[s[left]] -= 1&#10;                if m[s[left]] == 0: del m[s[left]]&#10;                left += 1&#10;    return max_len</code></pre></details></td>
    </tr>
    <tr>
      <td>61</td>
      <td>Sw 61 Permutation In String<br><br></b> <a href='https://leetcode.com/problems/permutation-in-string/' target='_blank'>LeetCode 567</a></td>
      <td><b>Example 1:</b> Sliding Window + Frequency Array.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window of size `len(s1)` over `s2`. Maintain frequency arrays for `s1` and the current window in `s2`. Compare arrays at each step.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">bool checkInclusion(string s1, string s2) {&#10;    if(s1.length() &gt; s2.length()) return false;&#10;    vector&lt;int&gt; count1(26, 0), count2(26, 0);&#10;    for(int i = 0; i &lt; s1.length(); i++) {&#10;        count1[s1[i] - &#x27;a&#x27;]++;&#10;        count2[s2[i] - &#x27;a&#x27;]++;&#10;    }&#10;    if(count1 == count2) return true;&#10;    for(int i = s1.length(); i &lt; s2.length(); i++) {&#10;        count2[s2[i] - &#x27;a&#x27;]++;&#10;        count2[s2[i - s1.length()] - &#x27;a&#x27;]--;&#10;        if(count1 == count2) return true;&#10;    }&#10;    return false;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def checkInclusion(s1, s2):&#10;    if len(s1) &gt; len(s2): return False&#10;    c1, c2 = [0]*26, [0]*26&#10;    for i in range(len(s1)):&#10;        c1[ord(s1[i]) - 97] += 1&#10;        c2[ord(s2[i]) - 97] += 1&#10;    if c1 == c2: return True&#10;    for i in range(len(s1), len(s2)):&#10;        c2[ord(s2[i]) - 97] += 1&#10;        c2[ord(s2[i - len(s1)]) - 97] -= 1&#10;        if c1 == c2: return True&#10;    return False</code></pre></details></td>
    </tr>
    <tr>
      <td>62</td>
      <td>Sw 62 Sliding Window Maximum<br><br></b> <a href='https://leetcode.com/problems/sliding-window-maximum/' target='_blank'>LeetCode 239</a></td>
      <td><b>Example 1:</b> Deque.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td>Deque</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a double-ended queue (deque) to store indices. Maintain indices in the deque such that the elements they correspond to are in decreasing order. The front of the deque will always be the maximum for the current window. Remove indices from the front if they are out of the window (`i - k`).<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; maxSlidingWindow(vector&lt;int&gt;&amp; nums, int k) {&#10;    deque&lt;int&gt; dq;&#10;    vector&lt;int&gt; ans;&#10;    for(int i = 0; i &lt; nums.size(); i++) {&#10;        if(!dq.empty() &amp;&amp; dq.front() == i - k) dq.pop_front();&#10;        while(!dq.empty() &amp;&amp; nums[dq.back()] &lt; nums[i]) dq.pop_back();&#10;        dq.push_back(i);&#10;        if(i &gt;= k - 1) ans.push_back(nums[dq.front()]);&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">from collections import deque&#10;def maxSlidingWindow(nums, k):&#10;    dq = deque()&#10;    ans = []&#10;    for i in range(len(nums)):&#10;        if dq and dq[0] == i - k: dq.popleft()&#10;        while dq and nums[dq[-1]] &lt; nums[i]: dq.pop()&#10;        dq.append(i)&#10;        if i &gt;= k - 1: ans.append(nums[dq[0]])&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>63</td>
      <td>Sw 63 Minimum Size Subarray Sum<br><br></b> <a href='https://leetcode.com/problems/minimum-size-subarray-sum/' target='_blank'>LeetCode 209</a></td>
      <td><b>Example 1:</b> Sliding Window.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window. Add elements to `sum`. While `sum >= target`, update `min_len` and subtract `nums[left]` from `sum`, incrementing `left`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int minSubArrayLen(int target, vector&lt;int&gt;&amp; nums) {&#10;    int left = 0, minLen = INT_MAX, sum = 0;&#10;    for(int right = 0; right &lt; nums.size(); right++) {&#10;        sum += nums[right];&#10;        while(sum &gt;= target) {&#10;            minLen = min(minLen, right - left + 1);&#10;            sum -= nums[left++];&#10;        }&#10;    }&#10;    return minLen == INT_MAX ? 0 : minLen;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def minSubArrayLen(target, nums):&#10;    left, minLen, sum_val = 0, float(&#x27;inf&#x27;), 0&#10;    for right in range(len(nums)):&#10;        sum_val += nums[right]&#10;        while sum_val &gt;= target:&#10;            minLen = min(minLen, right - left + 1)&#10;            sum_val -= nums[left]&#10;            left += 1&#10;    return 0 if minLen == float(&#x27;inf&#x27;) else minLen</code></pre></details></td>
    </tr>
    <tr>
      <td>64</td>
      <td>Sw 64 First Negative Integer In Every Window Of Size K<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Queue.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td>Queue</td>
      <td>-</td>
      <td><b>Explanation:</b> Maintain a queue of negative integers in the current window. While moving the window, add new negative integers, remove old ones out of window. The front of queue is the first negative.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;long long&gt; printFirstNegativeInteger(long long int A[], long long int N, long long int K) {&#10;    vector&lt;long long&gt; ans;&#10;    queue&lt;long long&gt; q;&#10;    for(long long i = 0; i &lt; K - 1; i++) {&#10;        if(A[i] &lt; 0) q.push(A[i]);&#10;    }&#10;    for(long long i = K - 1; i &lt; N; i++) {&#10;        if(A[i] &lt; 0) q.push(A[i]);&#10;        if(!q.empty()) ans.push_back(q.front());&#10;        else ans.push_back(0);&#10;        if(A[i - K + 1] &lt; 0 &amp;&amp; !q.empty() &amp;&amp; q.front() == A[i - K + 1]) q.pop();&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">from collections import deque&#10;def printFirstNegativeInteger(A, N, K):&#10;    ans = []&#10;    q = deque()&#10;    for i in range(K - 1):&#10;        if A[i] &lt; 0: q.append(A[i])&#10;    for i in range(K - 1, N):&#10;        if A[i] &lt; 0: q.append(A[i])&#10;        ans.append(q[0] if q else 0)&#10;        if A[i - K + 1] &lt; 0 and q and q[0] == A[i - K + 1]: q.popleft()&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>65</td>
      <td>Sw 65 Count Occurrences Of Anagrams<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/count-occurences-of-anagrams1536/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Sliding Window + Frequency Map.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Use a sliding window of size `pat.length()`. Keep frequency map of `pat`. Track `count` of distinct characters to match. While moving window, decrease `count` if char frequency matches. If `count == 0`, increment answer.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">int search(string pat, string txt) {&#10;    unordered_map&lt;char, int&gt; m;&#10;    for(char c : pat) m[c]++;&#10;    int count = m.size(), ans = 0, k = pat.length();&#10;    int i = 0, j = 0;&#10;    while(j &lt; txt.length()) {&#10;        if(m.find(txt[j]) != m.end()) {&#10;            m[txt[j]]--;&#10;            if(m[txt[j]] == 0) count--;&#10;        }&#10;        if(j - i + 1 &lt; k) j++;&#10;        else if(j - i + 1 == k) {&#10;            if(count == 0) ans++;&#10;            if(m.find(txt[i]) != m.end()) {&#10;                m[txt[i]]++;&#10;                if(m[txt[i]] == 1) count++;&#10;            }&#10;            i++; j++;&#10;        }&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def search(pat, txt):&#10;    m = {}&#10;    for c in pat: m[c] = m.get(c, 0) + 1&#10;    count, ans, k = len(m), 0, len(pat)&#10;    i = 0&#10;    for j in range(len(txt)):&#10;        if txt[j] in m:&#10;            m[txt[j]] -= 1&#10;            if m[txt[j]] == 0: count -= 1&#10;        if j - i + 1 == k:&#10;            if count == 0: ans += 1&#10;            if txt[i] in m:&#10;                m[txt[i]] += 1&#10;                if m[txt[i]] == 1: count += 1&#10;            i += 1&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>66</td>
      <td>Sw 66 Maximum Of All Subarrays Of Size K<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Deque.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(K)</td>
      <td>Deque</td>
      <td>-</td>
      <td><b>Explanation:</b> Same as LeetCode 239. Use a deque to maintain decreasing order of elements in the current window.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">vector&lt;int&gt; max_of_subarrays(int *arr, int n, int k) {&#10;    deque&lt;int&gt; dq;&#10;    vector&lt;int&gt; ans;&#10;    for(int i = 0; i &lt; n; i++) {&#10;        if(!dq.empty() &amp;&amp; dq.front() == i - k) dq.pop_front();&#10;        while(!dq.empty() &amp;&amp; arr[dq.back()] &lt;= arr[i]) dq.pop_back();&#10;        dq.push_back(i);&#10;        if(i &gt;= k - 1) ans.push_back(arr[dq.front()]);&#10;    }&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">from collections import deque&#10;def max_of_subarrays(arr, n, k):&#10;    dq = deque()&#10;    ans = []&#10;    for i in range(n):&#10;        if dq and dq[0] == i - k: dq.popleft()&#10;        while dq and arr[dq[-1]] &lt;= arr[i]: dq.pop()&#10;        dq.append(i)&#10;        if i &gt;= k - 1: ans.append(arr[dq[0]])&#10;    return ans</code></pre></details></td>
    </tr>
    <tr>
      <td>67</td>
      <td>Sw 67 Smallest Window In A String Containing All The Characters Of Another String<br><br></b> <a href='https://practice.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/1' target='_blank'>GFG</a></td>
      <td><b>Example 1:</b> Sliding Window.</td>
      <td><b>Time:</b> O(N)<br><b>Space:</b> O(1)</td>
      <td>-</td>
      <td>-</td>
      <td><b>Explanation:</b> Same as Minimum Window Substring. Use frequency map of `P` and a sliding window over `S`. Shrink window from left when all characters match to find the minimum length.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">string smallestWindow (string s, string p) {&#10;    if(p.length() &gt; s.length()) return &quot;-1&quot;;&#10;    unordered_map&lt;char, int&gt; m;&#10;    for(char c : p) m[c]++;&#10;    int count = m.size(), i = 0, j = 0, minLen = INT_MAX, start = 0;&#10;    while(j &lt; s.length()) {&#10;        if(m.find(s[j]) != m.end()) {&#10;            m[s[j]]--;&#10;            if(m[s[j]] == 0) count--;&#10;        }&#10;        while(count == 0) {&#10;            if(j - i + 1 &lt; minLen) {&#10;                minLen = j - i + 1;&#10;                start = i;&#10;            }&#10;            if(m.find(s[i]) != m.end()) {&#10;                m[s[i]]++;&#10;                if(m[s[i]] &gt; 0) count++;&#10;            }&#10;            i++;&#10;        }&#10;        j++;&#10;    }&#10;    if(minLen == INT_MAX) return &quot;-1&quot;;&#10;    return s.substr(start, minLen);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def smallestWindow(s, p):&#10;    if len(p) &gt; len(s): return &quot;-1&quot;&#10;    m = {}&#10;    for c in p: m[c] = m.get(c, 0) + 1&#10;    count, minLen, start, i = len(m), float(&#x27;inf&#x27;), 0, 0&#10;    for j in range(len(s)):&#10;        if s[j] in m:&#10;            m[s[j]] -= 1&#10;            if m[s[j]] == 0: count -= 1&#10;        while count == 0:&#10;            if j - i + 1 &lt; minLen:&#10;                minLen = j - i + 1&#10;                start = i&#10;            if s[i] in m:&#10;                m[s[i]] += 1&#10;                if m[s[i]] &gt; 0: count += 1&#10;            i += 1&#10;    return &quot;-1&quot; if minLen == float(&#x27;inf&#x27;) else s[start:start+minLen]</code></pre></details></td>
    </tr>
  </tbody>
</table>
