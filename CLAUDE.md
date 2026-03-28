# バックギャモンニュース プロジェクト

## 目的
バックギャモンの大会・例会・グッズ情報を自動収集し、Note.com用の記事下書きを生成するメディアシステム。

## フォルダ構成
```
backgammonnews/
├── research/          調査済み情報源サイト一覧
├── flows/             ワークフロー定義（調査対象・ティア構成・頻度）
│   └── logs/          自動収集ログ（リモートエージェントが追記）
├── drafts/            Note.com用下書きMarkdown（リモートエージェントが生成）
└── post_templates/    記事テンプレート（手動執筆時に参照）
```

## 重要ファイル
- `flows/tournament_flow.md` : トーナメント調査のティア構成（Tier1〜3）
- `flows/goods_flow.md` : グッズ情報調査フロー
- `research/tournament_sites.md` : 監視対象トーナメントサイト一覧
- `research/goods_sites.md` : 監視対象グッズサイト一覧

## 自動化（リモートエージェント）
- GitHub リポジトリ: hbk1123/backgammonnews
- スケジュール: 毎週月曜日 UTC 0:00（日本時間 月曜 9:00）
- 動作: 各サイトをWebSearch/WebFetchで調査 → logs/に追記 → drafts/に下書き生成 → git push
- 管理URL: https://claude.ai/code/scheduled

## 調査ティア構成
| ティア | 頻度 | 主なサイト |
|--------|------|----------|
| Tier1 | 毎週 | JBS, WBIF, IBF, INBC, sportnardy.info |
| Tier2 | 月2回（1日・15日） | Japan Open, UKBGF, USBGF, WBA, WBF, Chicago Open, WBGF 等 |
| Tier3 | 月1回（1日） | FmGammon Calendar, Chicago Point, WBGF結果DB |

## 日本人主要選手（調査時に優先確認）
Mochy（望月裕一）、Yazawa（矢沢亲将）、Mizutani Sam、Michi Kageyama

## Note.com投稿フロー
1. リモートエージェントが `drafts/YYYY-MM-DD-weekly.md` を生成
2. `git pull` でローカルに取得
3. 内容を確認・編集してNote.comに手動コピーペースト
