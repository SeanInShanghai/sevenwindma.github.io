---
title: Longest common prefix
date: 2018-01-09 00:00:00
categories:
- test/test
tags:
---

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
