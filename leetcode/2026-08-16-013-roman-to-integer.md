---
date: 2026-08-16
problem_id: 13
title: Roman to Integer
difficulty: Easy
url: https://leetcode.com/problems/roman-to-integer/
tags: []
status: solved # solved | attempted | review
time_spent_min: 30
---

# Roman to Integer

## 問題の要約

ローマ数字を整数に変換する

## 初見の印象

左から足していくのが基本だけど、4とかの例外は面倒くさそう

## アプローチ

### 方針

左側に小さい数字がくるパターンを整理して愚直に分岐させる。 with claudeくん

### 手順

1. 例外パターンを出す
2. 左側から足していくコードを組み立てる
3. 例外のときは分岐させる

## 解法

```java
class Solution {
    public int romanToInt(String s) {
        int convertedInteger = 0;
        Map<Character, Integer> romanMap = new HashMap<>();
        setUpRomanMap(romanMap);
        for (int i = 0; i < s.length(); i++) {
            int current = romanMap.get(s.charAt(i));

            if (i < s.length() - 1) {
                int next = romanMap.get(s.charAt(i + 1));
                if (current < next) {
                    convertedInteger += (next - current);
                    i++;
                    continue;
                }
            }
            convertedInteger += current;
        }
        return convertedInteger;
    }

    void setUpRomanMap(Map<Character, Integer> romanMap) {
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);
    }
}
```

## 計算量

| | |
|---|---|
| 時間 | O() |
| 空間 | O() |

## つまずいた点

どうやって例外を処理するか悩んだ

## 学んだこと

なし。愚直にやるだけ。  
ローマ数字とのMapを作るのは学んだ。

## 解説メモ

ない

## 別解・改善案

右から見ていくと、`i++`が一行なくなるので、実行速度が早いらしい。
たしかに、最初に提出したコードが6msに対して、こっちは4msだった。

```java
class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> romanMap = new HashMap<>();
        setUpRomanMap(romanMap);
        int total = 0;
        int prevValue = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            int current = romanMap.get(s.charAt(i));
            if (current < prevValue) {
                total -= current;
            } else {
                total += current;
            }
            prevValue = current;
        }
        return total;
    }

    void setUpRomanMap(Map<Character, Integer> romanMap) {
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);
    }
}
```

## 関連問題

- [ ] 

## 復習

| 日付 | メモ |
|------|------|
| YYYY-MM-DD | 初回 |
