# Strings Revision Table

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
      <td rowspan="1">1</td>
      <td rowspan="1">Str 01 Reverse A String<br><br></b> <a href='https://leetcode.com/problems/reverse-string/' target='_blank'>LeetCode 344</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: s = ["h","e","l","l","o"], Output: ["o","l","l","e","h"]<br><br><b>Note (Constraint):</b> Must be done in O(1) extra memory.</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(1) (Constraint)</td>
      <td><code>std::swap</code></td>
      <td><b>Immutability:</b> Python strings are immutable; must convert to list first if strictly following in-place rules, or use slicing `s[::-1]` which uses `O(N)` space.</td>
      <td><b>Explanation:</b> Use two pointers, one at the beginning and one at the end, swapping characters until they meet.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;vector&gt;&#10;#include &lt;utility&gt;&#10;&#10;void reverseString(std::vector&lt;char&gt;&amp; s) {&#10;    int left = 0, right = s.size() - 1;&#10;    while(left &lt; right) {&#10;        std::swap(s[left], s[right]);&#10;        left++;&#10;        right--;&#10;    }&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def reverse_string(s: list[str]) -&gt; None:&#10;    left, right = 0, len(s) - 1&#10;    while left &lt; right:&#10;        s[left], s[right] = s[right], s[left]&#10;        left += 1&#10;        right -= 1</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="2">2</td>
      <td rowspan="2">Str 02 Check Palindrome<br><br></b> <a href='https://leetcode.com/problems/valid-palindrome/' target='_blank'>LeetCode 125</a></td>
      <td rowspan="2"><b>Example 1:</b> Input: s = "A man, a plan, a canal: Panama", Output: true<br><br><b>Note (Constraint):</b> 1 &le; N &le; 2 * 10<sup>5</sup></td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td>Extra String Allocation</td>
      <td>-</td>
      <td><b>Explanation:</b> Clean the string to remove non-alphanumeric characters, convert to lowercase, and check if it equals its reverse.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;cctype&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;bool isPalindromeBrute(std::string s) {&#10;    std::string clean = &quot;&quot;;&#10;    for(char c : s) {&#10;        if(std::isalnum(c)) clean += std::tolower(c);&#10;    }&#10;    std::string rev = clean;&#10;    std::reverse(rev.begin(), rev.end());&#10;    return clean == rev;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def is_palindrome_brute(s: str) -&gt; bool:&#10;    clean = &quot;&quot;.join(c.lower() for c in s if c.isalnum())&#10;    return clean == clean[::-1]</code></pre></details></td>
    </tr>
    <tr>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(1) (Constraint)</td>
      <td><code>std::isalnum</code> / <code>.isalnum()</code></td>
      <td><b>Pointer Bounds:</b> Must ensure `left < right` inside inner `while` loops to prevent out-of-bounds on entirely non-alphanumeric strings.</td>
      <td><b>Explanation:</b> Two-pointer approach skipping non-alphanumeric characters in a single pass without extra memory.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;cctype&gt;&#10;&#10;bool isPalindromeOptimal(std::string s) {&#10;    int left = 0, right = s.length() - 1;&#10;    while(left &lt; right) {&#10;        while(left &lt; right &amp;&amp; !std::isalnum(s[left])) left++;&#10;        while(left &lt; right &amp;&amp; !std::isalnum(s[right])) right--;&#10;        if(std::tolower(s[left]) != std::tolower(s[right])) return false;&#10;        left++; right--;&#10;    }&#10;    return true;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def is_palindrome_optimal(s: str) -&gt; bool:&#10;    left, right = 0, len(s) - 1&#10;    while left &lt; right:&#10;        while left &lt; right and not s[left].isalnum(): left += 1&#10;        while left &lt; right and not s[right].isalnum(): right -= 1&#10;        if s[left].lower() != s[right].lower(): return False&#10;        left += 1; right -= 1&#10;    return True</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="2">3</td>
      <td rowspan="2">Str 03 Valid Anagram<br><br></b> <a href='https://leetcode.com/problems/valid-anagram/' target='_blank'>LeetCode 242</a></td>
      <td rowspan="2"><b>Example 1:</b> Input: s = "anagram", t = "nagaram", Output: true<br><br><b>Note (Constraint):</b> Strings consist of lowercase English letters.</td>
      <td><b>Time:</b> O(N log N) (Trade-off)<br><b>Space:</b> O(1) or O(N) (Language dependent)</td>
      <td><code>std::sort</code></td>
      <td><b>Length Check:</b> Immediately return false if lengths differ.</td>
      <td><b>Explanation:</b> Sort both strings and compare if they are identical.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;bool isAnagramBrute(std::string s, std::string t) {&#10;    if(s.length() != t.length()) return false;&#10;    std::sort(s.begin(), s.end());&#10;    std::sort(t.begin(), t.end());&#10;    return s == t;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def is_anagram_brute(s: str, t: str) -&gt; bool:&#10;    if len(s) != len(t): return False&#10;    return sorted(s) == sorted(t)</code></pre></details></td>
    </tr>
    <tr>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(1) (Constraint)</td>
      <td>-</td>
      <td><b>ASCII Mapping:</b> `char - 'a'` safely maps lowercase letters to `0-25`.</td>
      <td><b>Explanation:</b> Use a fixed size frequency array (Hash Map) to count character occurrences.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;vector&gt;&#10;&#10;bool isAnagramOptimal(std::string s, std::string t) {&#10;    if(s.length() != t.length()) return false;&#10;    std::vector&lt;int&gt; count(26, 0);&#10;    for(int i = 0; i &lt; s.length(); i++) {&#10;        count[s[i] - &#x27;a&#x27;]++;&#10;        count[t[i] - &#x27;a&#x27;]--;&#10;    }&#10;    for(int c : count) {&#10;        if(c != 0) return false;&#10;    }&#10;    return true;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def is_anagram_optimal(s: str, t: str) -&gt; bool:&#10;    if len(s) != len(t): return False&#10;    count = [0] * 26&#10;    for i in range(len(s)):&#10;        count[ord(s[i]) - ord(&#x27;a&#x27;)] += 1&#10;        count[ord(t[i]) - ord(&#x27;a&#x27;)] -= 1&#10;    for c in count:&#10;        if c != 0: return False&#10;    return True</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="1">4</td>
      <td rowspan="1">Str 04 Isomorphic Strings<br><br></b> <a href='https://leetcode.com/problems/isomorphic-strings/' target='_blank'>LeetCode 205</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: s = "egg", t = "add", Output: true<br><br><b>Note (Constraint):</b> 1 &le; N &le; 5 * 10<sup>4</sup></td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(1) (Constraint)</td>
      <td>-</td>
      <td><b>Full ASCII Range:</b> Size 256 array used to cover all possible ASCII characters, keeping space strict `O(1)`.</td>
      <td><b>Explanation:</b> Use two arrays to map characters from `s -> t` and `t -> s` ensuring a 1-to-1 bijective mapping.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;vector&gt;&#10;&#10;bool isIsomorphic(std::string s, std::string t) {&#10;    if(s.length() != t.length()) return false;&#10;    std::vector&lt;int&gt; mapST(256, -1);&#10;    std::vector&lt;int&gt; mapTS(256, -1);&#10;    &#10;    for(int i = 0; i &lt; s.length(); i++) {&#10;        char c1 = s[i], c2 = t[i];&#10;        if(mapST[c1] != -1 &amp;&amp; mapST[c1] != c2) return false;&#10;        if(mapTS[c2] != -1 &amp;&amp; mapTS[c2] != c1) return false;&#10;        mapST[c1] = c2;&#10;        mapTS[c2] = c1;&#10;    }&#10;    return true;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def is_isomorphic(s: str, t: str) -&gt; bool:&#10;    if len(s) != len(t): return False&#10;    mapST, mapTS = {}, {}&#10;    for c1, c2 in zip(s, t):&#10;        if (c1 in mapST and mapST[c1] != c2) or (c2 in mapTS and mapTS[c2] != c1):&#10;            return False&#10;        mapST[c1] = c2&#10;        mapTS[c2] = c1&#10;    return True</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="1">5</td>
      <td rowspan="1">Str 05 Longest Common Prefix<br><br></b> <a href='https://leetcode.com/problems/longest-common-prefix/' target='_blank'>LeetCode 14</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: strs = ["flower","flow","flight"], Output: "fl"<br><br><b>Note (Constraint):</b> 1 &le; strs.length &le; 200</td>
      <td><b>Time:</b> O(N log N * M) (Trade-off)<br><b>Space:</b> O(1)</td>
      <td><code>std::sort</code></td>
      <td><b>String Sorting Magic:</b> Alphabetical sorting forces the most differing strings to the ends.</td>
      <td><b>Explanation:</b> Sort the array of strings. The longest common prefix of the entire array must be the common prefix of the first and last strings in the sorted array.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;vector&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;std::string longestCommonPrefix(std::vector&lt;std::string&gt;&amp; strs) {&#10;    if(strs.empty()) return &quot;&quot;;&#10;    std::sort(strs.begin(), strs.end());&#10;    std::string first = strs[0];&#10;    std::string last = strs.back();&#10;    int i = 0;&#10;    while(i &lt; first.length() &amp;&amp; i &lt; last.length() &amp;&amp; first[i] == last[i]) {&#10;        i++;&#10;    }&#10;    return first.substr(0, i);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def longest_common_prefix(strs: list[str]) -&gt; str:&#10;    if not strs: return &quot;&quot;&#10;    strs.sort()&#10;    first, last = strs[0], strs[-1]&#10;    i = 0&#10;    while i &lt; len(first) and i &lt; len(last) and first[i] == last[i]:&#10;        i += 1&#10;    return first[:i]</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="1">6</td>
      <td rowspan="1">Str 06 Rotate String<br><br></b> <a href='https://leetcode.com/problems/rotate-string/' target='_blank'>LeetCode 796</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: s = "abcde", goal = "cdeab", Output: true<br><br><b>Note (Constraint):</b> 1 &le; s.length &le; 100</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Trade-off)</td>
      <td><code>.find()</code> / <code>in</code></td>
      <td><b>Concatenation Property:</b> `s + s` inherently contains every possible rotation of `s`.</td>
      <td><b>Explanation:</b> If s and goal have the same length, check if `goal` is a substring of `s + s`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;&#10;bool rotateString(std::string s, std::string goal) {&#10;    if(s.length() != goal.length()) return false;&#10;    std::string combined = s + s;&#10;    return combined.find(goal) != std::string::npos;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def rotate_string(s: str, goal: str) -&gt; bool:&#10;    if len(s) != len(goal): return False&#10;    return goal in (s + s)</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="1">7</td>
      <td rowspan="1">Str 07 Longest Palindromic Substring<br><br></b> <a href='https://leetcode.com/problems/longest-palindromic-substring/' target='_blank'>LeetCode 5</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: s = "babad", Output: "bab" (or "aba")<br><br><b>Note (Constraint):</b> 1 &le; s.length &le; 1000</td>
      <td><b>Time:</b> O(N<sup>2</sup>) (Constraint)<br><b>Space:</b> O(1) (Constraint)</td>
      <td>-</td>
      <td><b>Even/Odd Centers:</b> Must check `i, i` (odd) and `i, i+1` (even) to catch all palindrome types.</td>
      <td><b>Explanation:</b> Expand Around Center: For each character, treat it as the center of an odd and even length palindrome and expand outwards.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;algorithm&gt;&#10;&#10;std::string longestPalindrome(std::string s) {&#10;    if(s.empty()) return &quot;&quot;;&#10;    int start = 0, maxLen = 0;&#10;    auto expand = [&amp;](int l, int r) {&#10;        while(l &gt;= 0 &amp;&amp; r &lt; s.length() &amp;&amp; s[l] == s[r]) {&#10;            if(r - l + 1 &gt; maxLen) {&#10;                maxLen = r - l + 1;&#10;                start = l;&#10;            }&#10;            l--; r++;&#10;        }&#10;    };&#10;    for(int i = 0; i &lt; s.length(); i++) {&#10;        expand(i, i);     // Odd&#10;        expand(i, i + 1); // Even&#10;    }&#10;    return s.substr(start, maxLen);&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def longest_palindrome(s: str) -&gt; str:&#10;    if not s: return &quot;&quot;&#10;    start, max_len = 0, 0&#10;    def expand(l, r):&#10;        nonlocal start, max_len&#10;        while l &gt;= 0 and r &lt; len(s) and s[l] == s[r]:&#10;            if r - l + 1 &gt; max_len:&#10;                max_len = r - l + 1&#10;                start = l&#10;            l -= 1; r += 1&#10;            &#10;    for i in range(len(s)):&#10;        expand(i, i)     # Odd length&#10;        expand(i, i + 1) # Even length&#10;    return s[start:start+max_len]</code></pre></details></td>
    </tr>
    <tr>
      <td rowspan="1">8</td>
      <td rowspan="1">Str 08 String To Integer Atoi<br><br></b> <a href='https://leetcode.com/problems/string-to-integer-atoi/' target='_blank'>LeetCode 8</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: s = "   -42", Output: -42<br><br><b>Note (Constraint):</b> Prevent overflow using `INT_MAX/10` logic.</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(1)</td>
      <td><code>INT_MAX</code> / <code>INT_MIN</code></td>
      <td><b>Math Overflow check:</b> Check `res > INT_MAX / 10` before multiplying, same as Basic Maths chapter.</td>
      <td><b>Explanation:</b> Skip whitespaces, parse sign, and construct integer utilizing math bound checks before applying `x10`.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">#include &lt;string&gt;&#10;#include &lt;climits&gt;&#10;&#10;int myAtoi(std::string s) {&#10;    int i = 0, n = s.length(), sign = 1, res = 0;&#10;    while(i &lt; n &amp;&amp; s[i] == &#x27; &#x27;) i++; // Whitespace&#10;    if(i &lt; n &amp;&amp; (s[i] == &#x27;+&#x27; || s[i] == &#x27;-&#x27;)) {&#10;        sign = (s[i] == &#x27;-&#x27;) ? -1 : 1;&#10;        i++;&#10;    }&#10;    while(i &lt; n &amp;&amp; s[i] &gt;= &#x27;0&#x27; &amp;&amp; s[i] &lt;= &#x27;9&#x27;) {&#10;        int digit = s[i] - &#x27;0&#x27;;&#10;        if(res &gt; INT_MAX / 10 || (res == INT_MAX / 10 &amp;&amp; digit &gt; 7)) {&#10;            return sign == 1 ? INT_MAX : INT_MIN;&#10;        }&#10;        res = res * 10 + digit;&#10;        i++;&#10;    }&#10;    return res * sign;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python">def my_atoi(s: str) -&gt; int:&#10;    s = s.lstrip()&#10;    if not s: return 0&#10;    sign = -1 if s[0] == &#x27;-&#x27; else 1&#10;    if s[0] in [&#x27;-&#x27;, &#x27;+&#x27;]: s = s[1:]&#10;    &#10;    res = 0&#10;    for char in s:&#10;        if not char.isdigit(): break&#10;        res = res * 10 + int(char)&#10;        &#10;    res = sign * res&#10;    INT_MIN, INT_MAX = -2**31, 2**31 - 1&#10;    if res &lt; INT_MIN: return INT_MIN&#10;    if res &gt; INT_MAX: return INT_MAX&#10;    return res</code></pre></details></td>
    </tr>
  </tbody>
</table>
