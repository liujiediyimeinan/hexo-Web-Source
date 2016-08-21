title: 'LeetCode: Group Shifted Strings'
date: 2015-08-08 22:53:37
---
 Given a string, we can "shift" each of its letter to its successive letter, for example: "abc" -> "bcd". We can keep "shifting" which forms the sequence:

```
"abc" -> "bcd" -> ... -> "xyz"
```

Given a list of strings which contains only lowercase alphabets, group all strings that belong to the same shifting sequence.

### For example, 
given: `["abc", "bcd", "acef", "xyz", "az", "ba", "a", "z"]`, 
Return:
```
[
  ["abc","bcd","xyz"],
  ["az","ba"],
  ["acef"],
  ["a","z"]
]
```
***Note***: For the return value, each inner list's elements must follow the lexicographic order.

```java
public class Solution {
    public List<List<String>> groupStrings(String[] strings) {

        assert strings != null : "null array";

        List<List<String>> result = new ArrayList<>();
        Map<String, List<String>> map = new HashMap<>();

        for (String s : strings) {
            String code = getFeatureCode(s);
            List<String> val;
            if (!map.containsKey(code)) {
                val = new ArrayList<>();
            } else {
                val = map.get(code);
            }
            val.add(s);
            map.put(code, val);
        }

        for (String key : map.keySet()) {
            List<String> val = map.get(key);
            Collections.sort(val);
            result.add(val);
        }

        return result;
    }

    private String getFeatureCode(String s) {
        StringBuilder sb = new StringBuilder();
        sb.append("#");
        for (int i = 1; i < s.length(); i++) {
           int tmp = ((s.charAt(i) - s.charAt(i - 1)) + 26) % 26;
            sb.append(tmp).append("#");
        }
        return sb.toString();
    }
}
```