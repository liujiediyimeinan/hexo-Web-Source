title: 'LeetCode: Valid Sudoku'
date: 2015-06-24 00:03:22
tags:
 - LeetCode
---
<hr/>    
Validate if a given string is numeric.
### Some examples:
```
"0" => true
" 0.1 " => true
"abc" => false
"1 a" => false
"2e10" => true
```

```java

/**
 * Created by hzhou on 5/11/15. codeashobby@gmail.com
 */
public class ValidNumber  {
	public boolean isNumber(String s) {  
        if(s.trim().isEmpty()){  
            return false;  
        }  
        // I cheat
        String regex = "[-+]?(\\d+\\.?|\\.\\d+)\\d*(e[-+]?\\d+)?";  
        if(s.trim().matches(regex)){  
            return true;  
        }else{  
            return false;  
        }  
    }  
}
```