# グッズ新製品・セール情報 定期調査フロー

作成日：2026年3月28日
更新日：2026年3月28日

---

## 調査対象ソース

### 国内
| サイト名 | URL | 主な内容 | 自動調査 |
|---------|-----|---------|---------|
| JBS インターネットSHOP | https://backgammon.theshop.jp/ | 国内公式グッズ販売 | ✅ 月次 |

### 海外 総合ショップ（在庫・セール変動あり）
| サイト名 | URL | 主な内容 | 自動調査 |
|---------|-----|---------|---------|
| GammonVillage | https://www.gammonvillage.com/backgammon-shop/ | 最大手総合ショップ、多ブランド取扱 | ✅ 月次 |
| BGShop | https://bgshop.com/ | 専門ショップ | ✅ 月次 |
| Backgammon Galaxy Shop | https://shop.backgammongalaxy.com/ | Galaxy公式グッズ・定番品 | ✅ 月次 |
| Ace Point Backgammon | https://apbg.shop/ | 高級・限定品 | ✅ 月次 |
| Katgammon | https://katgammon.com/ | デザイン系アクセサリー（フィンランド） | ✅ 月次 |
| Gammon City | https://www.gammoncity.com/ | ジャンボボード・精密ダイス（ブルガリア） | ✅ 月次 |

### 海外 ボードメーカー直販（更新低頻度→四半期チェック）
| メーカー名 | URL | 価格帯 | 日本発送 | 自動調査 |
|-----------|-----|--------|---------|---------|
| Artgammon / Tavla Shop | https://www.artgammon.com/ | €400〜€1,000+ | 要確認 | ⬜ 四半期 |
| FmGammon Shop | https://www.fmgammon.com/ | $250〜$2,400 | 要確認 | ⬜ 四半期 |
| Theoboards | https://theoboards.com/ | 要確認 | ✅ 無料世界発送 | ⬜ 四半期 |
| Crisloid | https://www.crisloid.com/ | $25〜$350+ | 要確認 | ⬜ 四半期 |
| Manopoulos | https://www.manopoulos.com/ | €60〜€300+ | 代理店推奨 | ⬜ 四半期 |
| Hector Saxe | https://www.hectorsaxeparis.com/en | €数百〜数千 | ✅ JPY対応 | ⬜ 四半期 |
| Geoffrey Parker | https://www.geoffreyparker.com/ | £数百〜数万 | ✅ | ⬜ 四半期 |
| Alexandra Llewellyn | https://alexandrallewellyn.com/ | £500〜£5,200+ | ✅ 世界発送 | ⬜ 四半期 |
| Legacy Boards | https://legacyboardsbackgammon.com/ | 要確認 | 米国内のみ | ⬜ 四半期 |
| PRIMO | https://primobg.com/ | $1,495〜$1,750 | 要確認 | ⬜ 四半期 |
| Backgammon Travel Boards | https://backgammontravelboards.com/ | £300 | 要確認 | ⬜ 四半期 |
| Crisloid（アタッシェ） | https://www.crisloid.com/product-category/backgammon/attache-backgammon/ | $25〜$350+ | 要確認 | ⬜ 四半期 |
| Yenigün | https://www.yenigunbackgammon.com/ | 要確認 | 要確認 | ⬜ 四半期 |

### クロック・ダイスメーカー（半期チェック）
| メーカー名 | URL | 製品 | 価格帯 | 自動調査 |
|-----------|-----|------|--------|---------|
| DGT | https://digitalgametechnology.com/ | DGT1006タイマー | $40〜$65 | ⬜ 半期 |
| Tempest | https://tempestmodern.com/ | クロック各種 | $35〜$79 | ⬜ 半期 |
| NOVADICE | https://novadice.com/ | 精密ダイス | $55/4個 | ⬜ 半期 |
| DiceMan USA | https://dicemanusa.com/ | 精密ダイス | $13.45〜 | ⬜ 半期 |

---

## 収集する情報

- 新製品の発売・入荷告知
- セール・割引情報（期間・割引率）
- 限定品・コラボ商品の告知
- 廃番・在庫終了情報
- 日本向け送料・発送条件の変更

---

## スケジュール

| チェック種別 | 頻度 | 対象 |
|------------|------|------|
| 自動（月次） | 毎月第1週の月曜 | 国内 + 海外総合ショップ（7サイト） |
| 手動（四半期） | 1月・4月・7月・10月 | ボードメーカー直販（8サイト） |
| 手動（半期） | 1月・7月 | クロック・ダイスメーカー（4サイト） |

---

## 記録フォーマット（flows/logs/goods_hits.md）

```
### {調査日YYYY-MM-DD} - グッズ{月次/四半期/半期}調査

#### JBS SHOP
{発見した情報を箇条書き、または「更新なし」}

#### GammonVillage
{発見した情報を箇条書き、または「更新なし」}

#### BGShop
...

#### Backgammon Galaxy Shop
...

#### Ace Point Backgammon
...

#### Katgammon
...

#### Gammon City
...
```
