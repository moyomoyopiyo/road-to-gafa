---
date: 2026-08-23
problem_id: 14
title: Longest Common Prefix
difficulty: Easy
url: https://leetcode.com/problems/longest-common-prefix
tags: []
status: solved # solved | attempted | review
time_spent_min: 30
---

# {{title}}

## 問題の要約

与えられたStringの配列の単語に共通する接頭辞を抜き出して返す

## 初見の印象

愚直に先頭からの文字を見ていくんだな

## アプローチ

forで単語を一つずつ見ていき、starsWithで比較していく。
一致しなかったらsubstringで一文字ずつ減らしていく

### 方針

一番わかり易いとおもった

### 手順

1. 
2. 
3. 

## 解法

```java
// 使用言語: Java
class Solution {
    public String longestCommonPrefix(String[] strs) {

        String criteriaStr = strs[0];
        String longestCommonPrefix = strs[0];

        for (int i = 1; i < strs.length; i++) {

            while (!strs[i].startsWith(criteriaStr)) {
                criteriaStr = criteriaStr.substring(0, criteriaStr.length() - 1);
            }
            longestCommonPrefix = criteriaStr;
        }

        return longestCommonPrefix;
    }
}
```

## 計算量

| | |
|---|---|
| 時間 | O(m * n) |
| 空間 | O() |

## つまずいた点

starsWithを条件にしたwhileに辿り着くまでに時間がかかった

## 学んだこと

とくにない

## 解説メモ

<!-- 動画・Discussion・Editorial で気づいたこと -->

## 別解・改善案

### 縦スキャン

各文字列の中で一文字ずつ見ていくっていう方法。Claudeによると、好かれやすいロジックらしい。計算量は変わらんが、substringを何度も呼び出すよりマシ。

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";

        for (int i = 0; i < strs[0].length(); i++) {
            char c = strs[0].charAt(i);
            for (int j = 1; j < strs.length; j++) {
                // strs[j] がその位置まで届いていない、または文字が違う
                if (i == strs[j].length() || strs[j].charAt(i) != c) {
                    return strs[0].substring(0, i);
                }
            }
        }
        return strs[0];
    }
}
```

### 分割統治法

配列を半分に分割して、それぞれの半分のLongest Common Prefixを再帰的に求め、最後に２つを比較する。  
マージソートとかクイックソートと似た考え方。計算量は同じ。

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";
        return divide(strs, 0, strs.length - 1);
    }

    private String divide(String[] strs, int left, int right) {
        if (left == right) return strs[left];
        int mid = (left + right) / 2;
        String lcpLeft = divide(strs, left, mid);
        String lcpRight = divide(strs, mid + 1, right);
        return commonPrefix(lcpLeft, lcpRight);
    }

    private String commonPrefix(String a, String b) {
        int minLen = Math.min(a.length(), b.length());
        int i = 0;
        while (i < minLen && a.charAt(i) == b.charAt(i)) {
            i++;
        }
        return a.substring(0, i);
    }
}
```

## 関連問題

- [ ] 

## 復習

| 日付 | メモ |
|------|------|
| YYYY-MM-DD | 初回 |
