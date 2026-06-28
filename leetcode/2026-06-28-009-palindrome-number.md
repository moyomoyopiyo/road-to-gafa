---
date: 2026-06-28
problem_id: 9
title: Palindrome Number
difficulty: Easy
url: https://leetcode.com/problems/palindrome-number/
tags: [Math]
status: solved # solved | attempted | review
time_spent_min: 
---

# {{title}}

## 問題の要約

与えられた整数が回文かどうかを判定する

## 初見の印象

数字の回文か、なんか回分は一旦Stringにしようと思ったけど数学的になんかありそう

## アプローチ

### 方針

StringBuilderのreverse()を使うためにStringにぶち込んだ

### 手順

省略

## 解法

```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x < 0) {
            return false;
        }
        Integer xInt = Integer.valueOf(x);
        String xStr = xInt.toString();
        StringBuilder sb = new StringBuilder();
        sb.append(x);
        sb.reverse();
        String reversedX = sb.toString();
        return xStr.equals(reversedX);
    }
}
```

## 計算量

省略

## つまずいた点

`reverse()`の使い方が怪しかった

## 学んだこと

特になし

## 解説メモ

数学的な考えができるようになりたい

## 別解・改善案

Stringに変えるのは効率悪いらしい（そりゃそう）

```java
class Solution {
    public boolean isPalindrome(int x) {
        // Negative numbers are not palindromes
        if (x < 0) return false;
        
        // Numbers ending in 0 (except 0 itself) are not palindromes
        if (x % 10 == 0 && x != 0) return false;
        
        int reversed = 0;
        while (x > reversed) {
            reversed = reversed * 10 + x % 10;
            x /= 10;
        }
        
        // For odd-length numbers, middle digit doesn't matter
        return x == reversed || x == reversed / 10;
    }
}
```

## 関連問題

- [ ] 

## 復習

| 日付 | メモ |
|------|------|
| YYYY-MM-DD | 初回 |
