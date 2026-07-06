# pattern-radar (Roy Log)

XAU/USD のトレード配信(ロイさんのシグナル)を貼り付けて記録し、価格チャートと照合するための個人用ツール。単一ファイルの静的サイト。

## 構成

- `index.html` — アプリ本体(HTML/CSS/JSを1ファイルに全部書いている。ビルド不要)
- `icon.svg` / `icon-180.png` — PWA用アイコン
- GitHub Pagesが`main`ブランチの`index.html`をそのまま配信 → https://hoshi2.github.io/pattern-radar/

## 主な機能

- 「貼る」タブ: 配信テキストをパースしてロング/ショートのゾーン・条件ライン・利確ターゲットを自動抽出(`parseRoy()`)
- 「タイムライン」タブ: 保存した配信を日付ごとに一覧表示、TwelveData APIで実際の値動きと照合してステータス判定
- 「チャート」タブ: lightweight-charts でローソク足を表示し、ゾーン/TPをオーバーレイ
- 「設定」タブ: TwelveData APIキー、Supabaseクラウド同期(テーブル`roy_log`)、JSONバックアップ

## データ保存

- ブラウザの`localStorage`が正(オフラインでも動く)
- Supabase接続時は`roy_log`テーブルに`payload`としてJSON丸ごと保存し、端末間で同期

## 開発メモ

- 外部依存はCDN読み込みのみ(lightweight-charts, TwelveData REST API, Supabase REST API)。npm/ビルドは無し
- 変更は`index.html`を直接編集するだけでOK
