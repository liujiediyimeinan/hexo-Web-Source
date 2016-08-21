title: 'LeetCode: Distinct Subsequences'
date: 2015-06-24 00:03:22
---
 Given a string S and a string T, count the number of distinct subsequences of T in S.

A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, "`ACE`" is a subsequence of "`ABCDE`" while "`AEC`" is not).

### Here is an example:
S = "`rabbbit`", T = "`rabbit`"
Return `3`.

```java
public class DistinctSubsequences {
    public int numDistinct(String s, String t) {
        assert s != null && t != null;
        if (s.length() < t.length()) {
            return 0;
        }
        int[][] map = new int[s.length() + 1][t.length() + 1];
        for (int i = 0; i <= s.length(); i++) {
            map[i][0] = 1;
        }
        for (int i = 1; i <= s.length(); i++) {
            for (int j = 1; j <= t.length(); j++) {
                if (s.charAt(i - 1) == t.charAt(j - 1)) {
                    map[i][j] = map[i - 1][j] + map[i - 1][j - 1];
                } else {
                    map[i][j] = map[i - 1][j];
                }
            }
        }
        return map[s.length()][t.length()];
    }
}
```

### Thanks @traceformula for the solution with less space:
```java
public int numDistinct(String s, String t) {
    if (s == null || t == null || t.isEmpty()) {
        return 0;
    }
    int[] dp = new int[t.length()];

    for (int i = 0; i < s.length(); i++) {
        char c = s.charAt(i);
        for (int j = dp.length - 1; j >= 0; j--) {
            if (c == t.charAt(j)) {
                dp[j] = dp[j] + (j != 0 ? dp[j - 1] : 1);
            }
        }
    }
    return dp[t.length() - 1];
}
```
