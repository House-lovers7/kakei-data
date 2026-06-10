# kakei-data

PWAアプリ「[家計の味方](https://food-price-radar.vercel.app)」のデータ配信リポジトリです。
GitHub Pages (https://house-lovers7.github.io/kakei-data) を通じて、アプリに以下のデータを配信しています。

## データ内容

| ファイル | 内容 |
|---|---|
| `initial-index.json` / `index-history.json` | 食品価格指数(CPIベース)の初期値・履歴 |
| `benchmark/*.json` | 楽天市場・Yahoo!ショッピング・小売チェーン等の価格ベンチマーク、値上げニュース集約 |
| `sales/daily-sales.json` | チラシ特売データ |
| `campaigns/convenience.json` | コンビニキャンペーン情報 |
| `categories.json` / `chains.json` / `regions.json` | カテゴリ・チェーン店・地域マスタ |
| `sale-rules.json` / `substitutions.json` / `recipes.json` | 特売ルール・代替品・レシピデータ |
| `manifest.json` | 配信ファイル一覧 |

## 更新頻度

自動バッチにより更新されます。

- 毎日 7:00 — 値上げニュース
- 日曜・水曜 6:00 — チラシ特売
- 日曜 3:00 — 価格ベンチマーク・価格指数

## 個人情報について

このリポジトリに **個人情報・ユーザーデータは一切含まれません**。
配信されるのは公開情報を集約した価格・商品・店舗データのみです。

## ライセンス

データは [CC BY 4.0](LICENSE) で提供します。利用時は「家計の味方 (kakei-data)」のクレジット表記をお願いします。

## セキュリティ

脆弱性やデータの問題を発見した場合は [SECURITY.md](SECURITY.md) をご覧ください。
