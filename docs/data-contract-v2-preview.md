# データ契約 v2 予告（preview）

> 作成: 2026-07-19 / 状態: 方向性承認済み・実装未着手
> 設計の正本はアプリ本体リポジトリ（food_price_radar）の
> `docs/design/zero-base-architecture.md` §4.4 と `docs/engineering/03_adrs/ADR-0004-data-contract-v2.md`。
> 本書はデータ利用者向けの短い告知であり、仕様の原本ではない。

## 何が変わる予定か

現行のルート直下レイアウト（`initial-index.json`, `benchmark/*.json` 等）は**暗黙の v1** として当面配信を継続します。
新レイアウトは将来 `v2/` 配下に並行配信されます:

```
v2/
  manifest.json                     # 品質メタデータ付き（updatedAt / contentAsOf / status / quality / contentHash / schemaVersion）
  master/                           # 低頻度マスタ（categories / chains / regions / products）
  facts/{category}/latest.json      # カテゴリ別分割 — 必要カテゴリだけ取得可能
  facts/{category}/YYYY-MM.json     # 追記型の月次履歴
  events/price-events-YYYY-MM.json  # 値上げ・ステルス値上げ検知イベント
schemas/v2/*.schema.json            # JSON Schema（データ契約の外部参照用）
```

## 利用者への約束（v2 契約）

- **v2 内は additive-only**: フィールド追加のみ。削除・型変更は行わず、必要な場合は v3 を新設して並行配信します
- **廃止予定は事前告知**: manifest の `deprecations[]` で告知します
- **鮮度の明示**: ファイルごとに `contentAsOf`（データ自体の鮮度）と `status`（fresh / stale / degraded）を配信します
- **品質ゲート通過データのみ配信**: スキーマ検証・参照整合・異常値検知を通過したデータだけが publish されます
- ライセンスは現行どおり **CC BY 4.0**（クレジット: 「家計の味方 (kakei-data)」）を継続します

## 現行 v1 の扱い

- v2 安定までルート直下の配信は変更しません
- v1 凍結（更新停止）の際は、本リポジトリの README と本書で事前に告知します
