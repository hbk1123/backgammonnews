# 週次調査 マスタープロンプト

作成日：2026-03-29

このファイルはリモートエージェント（スケジュール実行）用のプロンプト定義です。
claude.ai/code のスケジュール設定にこのプロンプトを貼り付けて使用します。

---

## スケジュール設定

- **トリガー**: 毎週月曜 UTC 0:00（日本時間 月曜 9:00）
- **リポジトリ**: hbk1123/backgammonnews

---

## プロンプト本文

```
今日の日付を確認し、以下の調査パターンに従って実行してください。
作業ディレクトリ：/c/Users/hibik/backgammonnews（またはリポジトリルート）

## STEP 0: 実行パターンの決定

今日の日付（YYYY-MM-DD）を取得し、以下のフラグを決定する：

- RUN_TIER1 = 常にtrue
- RUN_TIER2 = 今日が月の1日または15日ならtrue
- RUN_TIER3 = 今日が月の1日ならtrue
- RUN_GOODS_MONTHLY = 今日が月の1日ならtrue
- RUN_GOODS_QUARTERLY = 今日が1月・4月・7月・10月の1日ならtrue
- RUN_GOODS_SEMIANNUAL = 今日が1月・7月の1日ならtrue
- RUN_REVIEW = 今日が月の1日ならtrue
- RUN_OSAKA = RUN_TIER2 かつ 今月が3月ならtrue（大阪オープンは毎年3月のみ）
- RUN_NAKAYOSHI_FEB = 今日が1月の1日ならtrue（2月のフェアリーギャモン大会告知確認）
- RUN_NAKAYOSHI_JUN = 今日が5月の1日ならtrue（6月のバックギャモン大会告知確認）

---

## STEP 1: トーナメント調査（Tier1・毎週必須）

以下をWebSearch/WebFetchで調査し、前回調査以降の新着情報を抽出する：

- JBS: https://backgammon.or.jp/
  - WebSearch「バックギャモン 大会 告知 site:backgammon.or.jp」でも補完
- WBIF: https://www.wbif.net/
- IBF: https://i-bg-federation.com/
- INBC: https://inbcgammon.wiki.fc2.com/
- sportnardy.info: https://sportnardy.info/
  （JSレンダリングのためWebFetch不可→WebSearch「backgammon tournament sportnardy」で補完）

日本人主要選手の情報を優先確認：
Mochy（望月裕一）、Yazawa（矢沢亲将）、Mizutani Sam、Michi Kageyama

---

## STEP 2: トーナメント調査（Tier2・月2回：1日・15日のみ）

RUN_TIER2 が true の場合のみ実行：

- Japan Open: https://festival.backgammon.or.jp/
- 大阪オープン: https://open.backgammon.osaka/ （RUN_OSAKA が true の場合のみ）
- UKBGF: https://ukbgf.com/
- USBGF: https://usbgf.org/
- WBA: https://www.world-backgammon-association.com/
- WBF: https://www.wbf.net/
- Chicago Open: https://chicagoopenbg.com/
- WBGF: https://wbgf.info/
- sportnardy.info（Tier1と兼用）

---

## STEP 3: トーナメント調査（Tier3・月1回：1日のみ）

RUN_TIER3 が true の場合のみ実行：

- FmGammon Calendar: https://www.fmgammon.com/backgammon-tournament-calendar.php
- Chicago Point: http://www.chicagopoint.com/
- WBGF結果DB: https://results.wbgf.info/tmanager
- なかよし村とゲームの木（mixi）: https://mixi.jp/view_community.pl?id=207561
  （RUN_NAKAYOSHI_FEB または RUN_NAKAYOSHI_JUN が true の場合のみ）

---

## STEP 4: 例会情報調査（毎週必須）

以下の3ステップで調査：

**Step 4-1: JBSカレンダー（WebSearch補完）**
WebSearch「バックギャモン 例会 {今月}{来月} site:backgammon.or.jp」

**Step 4-2: 非公認例会のX検索**
WebSearch「バックギャモン 例会 {今週〜2週間後の日付範囲}」
WebSearch「バックギャモン 例会 ねこまど OR 関内 OR 代官山 OR 四谷 OR 柏木 OR 将棋の森 2026」

**Step 4-3: 既知クラブの個別確認**
- 赤坂バックギャモン道場: https://bgakasaka.wordpress.com/
- ゲームスペース柏木: WebSearch「ゲームスペース柏木 バックギャモン 例会」
- 中村吉之氏（将棋の森・四谷）: WebSearch「bgyoshi バックギャモン 例会」
- 関内バックギャモンの会: WebSearch「関内バックギャモン 例会」

---

## STEP 5: グッズ調査（月次・1日のみ）

RUN_GOODS_MONTHLY が true の場合のみ実行：

- JBS SHOP: https://backgammon.theshop.jp/
- GammonVillage: https://www.gammonvillage.com/backgammon-shop/
- BGShop: https://bgshop.com/
- Backgammon Galaxy Shop: https://shop.backgammongalaxy.com/
- Ace Point Backgammon: https://apbg.shop/
- Katgammon: https://katgammon.com/
- Gammon City: https://www.gammoncity.com/

抽出項目：新製品・セール・入荷・廃番情報

---

## STEP 6: グッズ調査（四半期・1月4月7月10月のみ）

RUN_GOODS_QUARTERLY が true の場合のみ実行（STEP5に追加）：

ボードメーカー直販（Artgammon, FmGammon, Theoboards, Crisloid, Manopoulos,
Hector Saxe, Geoffrey Parker, Alexandra Llewellyn, Legacy Boards, PRIMO,
Backgammon Travel Boards, Bone Club, Yenigün）を各WebFetchで確認。

---

## STEP 7: グッズ調査（半期・1月7月のみ）

RUN_GOODS_SEMIANNUAL が true の場合のみ実行（STEP5に追加）：

クロック・ダイスメーカー（DGT, Tempest, NOVADICE, DiceMan USA）を確認。

---

## STEP 8: レビュー・コンテンツ調査（月1回・1日のみ）

RUN_REVIEW が true の場合のみ実行：

- Reddit r/backgammon: https://www.reddit.com/r/backgammon/
- Backgammon Galaxy YouTube: https://www.youtube.com/@BackgammonGalaxy
- Backgammon Forums: https://www.backgammonforums.com/
- WebSearch「#バックギャモン」で日本語X投稿を補完

---

## STEP 9: ログ記録

以下のファイルに追記（追記のみ・既存内容は削除しない）：

- flows/logs/tournament_hits.md：STEP1〜3の結果
- flows/logs/meetup_hits.md：STEP4の結果
- flows/logs/goods_hits.md：STEP5〜7の結果（RUN_GOODS_MONTHLY の場合のみ）
- flows/logs/review_hits.md：STEP8の結果（RUN_REVIEW の場合のみ）

---

## STEP 10: 下書き生成

`drafts/{今日の日付YYYY-MM-DD}-weekly.md` を新規作成する。

### 記事構成：
```
# バックギャモン週報 {年}年{月}月第{N}週

{日付}時点の情報です。

---

## トーナメント情報

### 国内大会
（告知中・直近の大会を優先。結果があれば優勝者を明記）

### 海外大会
（今後60日以内を中心に。日本人選手の参加・結果を優先記載）

---

## グッズ情報（月初のみ掲載）
（RUN_GOODS_MONTHLY の場合のみセクション追加）

---

## 例会・イベント情報

**今週末・来週の例会**
| 日時 | 名称 | 場所 | 備考 |

**定期例会**

---

*情報ソース：...*
```

### 記述ルール：
- 日本人選手名はローマ字+日本語で補記（例：Mochy（望月裕一））
- 信頼度が低い情報には「※要確認」を付記
- 大会結果がある場合は必ず優勝者を明記
- HTTP 403などで取得不可のサイトはWebSearchで補完し「（WebSearch経由）」と注記

---

## STEP 11: git push

```
git add flows/logs/ drafts/
git commit -m "chore: 週次調査＋下書き生成 {今日の日付YYYY-MM-DD}"
git push origin master
```
```

---

## 実行パターン早見表

| 月の日付 | Tier1 | Tier2 | Tier3 | グッズ月次 | グッズ四半期 | グッズ半期 | レビュー |
|---------|-------|-------|-------|-----------|------------|-----------|---------|
| 1日（1・7月） | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 1日（4・10月） | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ |
| 1日（その他） | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| 15日 | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| その他の月曜 | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
