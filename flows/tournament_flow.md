# トーナメント情報 定期調査フロー

作成日：2026年3月28日

---

## ティア構成

| ティア | チェック頻度 | 対象サイト |
|--------|------------|-----------|
| **Tier 1** | 毎週 | JBS、WBIF、IBF、INBC |
| **Tier 2** | 月2回（1日・15日） | Japan Open、大阪オープン、UKBGF、USBGF、WBA、WBF、Chicago Open、WBGF、sportnardy.info |
| **Tier 3** | 月1回（1日） | FmGammon Calendar、Chicago Point、WBGF結果DB |

---

## ティア昇降格基準

### 昇格条件（下位→上位）
- 直近3ヶ月で月平均3件以上の有益情報が取れた
- 日本人選手が関与する大会の主要発信源となった
- 速報性が他サイトより明らかに高いと判明した

### 降格条件（上位→下位）
- Tier 1 → Tier 2：3ヶ月連続でヒット0件、または更新停止
- Tier 2 → Tier 3：6ヶ月連続でヒット0件
- Tier 3 → アーカイブ：12ヶ月連続でヒット0件

---

## ティア見直しスケジュール

**四半期ごと（1月・4月・7月・10月の第1週）**に以下を実施：

1. 各サイトの直近3ヶ月のヒット件数を集計（`logs/tournament_hits.md` 参照）
2. 昇降格基準と照らし合わせてティアを見直す
3. 見直し結果をこのファイルの「ティア構成」テーブルに反映
4. 変更があれば `logs/tier_history.md` に記録

---

## 収集する情報の定義

**有益情報**と判定する基準：
- 今後60日以内に開催されるトーナメントの告知
- 大会結果（日本人選手のチェックを優先）
- レーティング更新・代表選考情報
- 新規大会・フォーマット変更の発表

---

## Claudeによる自動調査プロンプト（Tier 1用）

```
以下のサイトを調査し、前回調査（{前回日付}）以降の新着トーナメント情報をまとめてください。

対象サイト：
- JBS: https://backgammon.or.jp/
- WBIF: https://www.wbif.net/
- IBF: https://i-bg-federation.com/
- INBC: https://inbcgammon.wiki.fc2.com/

抽出項目：
- 大会名
- 開催日・場所（オンライン/オフライン）
- 参加資格・エントリー情報
- 日本人選手に関する情報

結果は flows/logs/tournament_hits.md に追記してください。
新着情報がなければ「更新なし」と記録してください。
```

---

## Claudeによる自動調査プロンプト（Tier 2・3用）

```
以下のサイトを調査し、前回調査（{前回日付}）以降の新着トーナメント情報をまとめてください。

対象サイト（Tier 2）：
- Japan Open: https://festival.backgammon.or.jp/
- 大阪オープン: https://open.backgammon.osaka/  ※毎年3月開催のみ。3月以外は調査スキップ可
- UKBGF: https://ukbgf.com/
- USBGF: https://usbgf.org/
- WBA: https://www.world-backgammon-association.com/
- WBF: https://www.wbf.net/
- Chicago Open: https://chicagoopenbg.com/
- WBGF: https://wbgf.info/
- sportnardy.info: https://sportnardy.info/

対象サイト（Tier 3）：
- FmGammon Calendar: https://www.fmgammon.com/backgammon-tournament-calendar.php
- Chicago Point: http://www.chicagopoint.com/
- WBGF結果DB: https://results.wbgf.info/tmanager
- なかよし村とゲームの木（mixi）: https://mixi.jp/view_community.pl?id=207561
  ※ 年2回のみ確認：1月（フェアリーギャモン大会・2月開催）・5月（バックギャモン大会・6月開催）

抽出項目・記録方法はTier 1と同様。
```
