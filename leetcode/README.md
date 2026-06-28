# LeetCode 学習ログ

問題を解いた記録を Markdown で残すフォルダです。

## 使い方

1. `_template.md` をコピーする
2. ファイル名を付ける（例: `2026-06-28-001-two-sum.md`）
3. フロントマターと各セクションを埋める

## ファイル名の例

```
YYYY-MM-DD-問題番号-スラッグ.md
```

- `2026-06-28-001-two-sum.md`
- `2026-06-28-217-contains-duplicate.md`

## フォルダ構成（任意）

日付で整理したい場合:

```
leetcode/
  2026/
    06/
      2026-06-28-001-two-sum.md
```

## ステータス

| status | 意味 |
|--------|------|
| `solved` | 自力またはヒント少なめで解けた |
| `attempted` | 挑戦したが未完了・解説を見た |
| `review` | 復習対象 |

## テンプレートのコピー

```bash
cp leetcode/_template.md "leetcode/$(date +%Y-%m-%d)-001-problem-name.md"
```
