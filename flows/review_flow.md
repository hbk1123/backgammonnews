# レビュー・コンテンツ情報収集フロー

作成日：2026年3月28日

---

## 調査対象ソース

### Reddit
| サブレディット | URL | 主な内容 |
|---------|-----|---------|
| r/backgammon | https://www.reddit.com/r/backgammon/ | 英語圏最大コミュニティ、レビュー・議論 |

### YouTube（主要チャンネル）
| チャンネル名 | 検索URL | 主な内容 |
|---------|-----|---------|
| Backgammon Galaxy | https://www.youtube.com/@BackgammonGalaxy | 講座・大会配信 |
| U.S. Backgammon Federation | https://www.youtube.com/@USBackgammonFederation | トーナメント生配信 |
| Backgammon is Beautiful | https://www.youtube.com/@BackgammonisBeautiful | 教育コンテンツ |

### Twitter/X（ハッシュタグ・アカウント）
| 対象 | 内容 |
|-----|-----|
| #backgammon | 英語圏の投稿全般 |
| #バックギャモン | 日本語投稿 |
| @JBS_Backgammon | JBS公式アカウント |

### フォーラム
| サイト名 | URL | 主な内容 |
|---------|-----|---------|
| Backgammon Forums | https://www.backgammonforums.com/ | 英語圏コミュニティ |

---

## 収集する情報

- 用具・ボードのレビュー投稿
- 新製品・新ルールへの反応・評価
- 話題になっているトピック・議論
- 日本語コンテンツの新規発信

---

## 自動化の範囲と限界

| ソース | 自動取得 | 備考 |
|--------|---------|------|
| Reddit | ○ | WebFetchで取得可能 |
| YouTube | △ | チャンネルページのみ取得可能（動画検索はAPIが必要） |
| Twitter/X | × | ログインが必要なため自動取得不可 → 手動確認 |
| フォーラム | ○ | WebFetchで取得可能 |

---

## スケジュール

月1回（毎月第1週の月曜日）、トーナメント調査と同一トリガー内で処理
Twitter/Xのみ手動確認

---

## 記録フォーマット（flows/logs/review_hits.md）

```
### {調査日YYYY-MM-DD} - レビュー月次調査

#### Reddit r/backgammon
{話題のトピック・レビュー投稿を箇条書き、または「特筆なし」}

#### YouTube（新着動画）
{新着動画タイトル・内容を箇条書き、または「特筆なし」}

#### Backgammon Forums
{話題のスレッドを箇条書き、または「特筆なし」}

#### Twitter/X（手動確認）
{未確認 / 確認済みの場合は内容を記載}
```
