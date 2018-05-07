
---
title: Hello World
date: 2018-01-12 00:18:00
categories:
- test/test
tags:
---

# 问题：最长公共前缀
## 描述：找到一个字符串数组中的最长公共前缀
### 分析：
前缀：就是从第一个字符开始，到后面的每一个字符，找到第一个相同的字符，然后从第二个字符开始，找到第二个相同的，如果一旦有不同，则跳出循环

### 思路：
找到最短的字符串，并且确定最短字符串的位置，从该字符串开始，每次截取一部分呢，从最长到最短。截取部分在输入的数组中比较，一旦有截取部分全部成功，则匹配成功，否则失败。

#### 代码

```
 public  String longestCommonPrefix(String[] strs){
        if(strs == null || strs.length == 0){
            return "";
        }
        if(strs.length == 1){
            return strs[0];
        }

        String result = "";

        //求strs最小的长度
        int minLen = strs[0].length();
        int minLenIndex = 0;
        for(int i = 0; i < strs.length; i++){
            if(strs[i].length() < minLen) {
                minLen = strs[i].length();
                minLenIndex = i;
            }
        }
        for(int j = minLen; j >=0; j--){
            result = strs[minLenIndex].substring(0, j);
            boolean allEqual = true;
            for(String s : strs){
                if(!s.substring(0, j).equals(result)){
                    allEqual = false;
                    break;
                }
            }
            if(allEqual){
                return result;
            }
        }



        return result;
    }
```
