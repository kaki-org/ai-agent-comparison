# 引き継ぎ：Cursor・Claude・Genspark 比較記事プロジェクト

## 私について・進め方の希望
- 敬語（です/ます）、結論ファースト、前置き不要
- コミットメッセージは「日本語1行＋空行＋3行程度の箇条書き」、Co-Authored-By は付けない

## プロジェクトの概要
- 目的: 同じプロンプトを Cursor・Claude（Claude Code）・Genspark に渡し、成果物を比較する記事を書く（Confluence に掲載予定）
- 実施日: 2026-10-30
- リポジトリ（public）: https://github.com/kaki-org/ai-agent-comparison
- 比較一覧（GitHub Pages）: https://kaki-org.github.io/ai-agent-comparison/
- 構成: `{claude,cursor,genspark}/{01-tetris,02-kaki-character,03-landing-page,04-slides}/{v1,final,log.md}`、`prompts/*.md`、`article/`

## 実験のルール（決定済み）
- 同一プロンプト（自然文＋最低限の要件3点）。03・04 は各ツールが 02 で作ったキャラを使う
- 一発目を v1、手直し後を final。手直しは最大2回 → 実績は全題材0回
- 評価: 客観指標（所要時間・手直し回数・そのまま動いたか・要件充足）＋見た目 ◎○△（筆者の主観、未記入）
- 条件: Claude = Claude Code 2.1.312 / Pro / claude-opus-5-5、Cursor = 3.27.22 / Pro / デフォルトの Grok 4.7 High Fast、Genspark = Super Agent / Plus
- Claude は ~/.claude/CLAUDE.md、Cursor は ~/AGENTS.md（いずれも検証重視の指示）を読み込んでいる

## 結果の要約
| | Claude | Cursor | Genspark |
|---|---|---|---|
| 01 テトリス | 約1分18秒 | 約23分 | 約7分 |
| 02 柿キャラ | 約50秒（かきまる） | 約1分（ぽて柿） | 約2分（かき丸） |
| 03 紹介 LP | 約1分31秒 | 約12分（取り直し後） | 約8分 |
| 04 スライド | 約2分44秒 | 約16分 | 約25分 |
| 合計 | 約6分23秒 | 約52分 | 約42分 |

- 全ツール・全題材で要件を満たし、手直し0回
- 違いは「速さ」「確認の仕方（Claude 軽く即修正／Cursor ブラウザで徹底確認／Genspark 途中で質問）」「キャラ名の引き継ぎ（Claude・Genspark 維持、Cursor はぽて柿→ポテガキ）」
- Genspark スライドは出典付きで情報量最多。ただし「刀根早生は早生の枝変わり」という誤り1か所（正しくは平核無の枝変わり）
- 3ツールとも栄養値（甘柿100gあたり VC 70mg 等）は八訂と一致

## 実験中のトラブルと対応
- Cursor の LP 1回目が上位フォルダから Claude の LP を読んでいたため不採用 → 作業フォルダを分離して取り直し
- Claude の LP はプロンプト貼り間違いで2回やり直し（比較には影響なし）
- Genspark の 02 で途中の質問に気づかず待ち時間が発生
- Genspark の LP に残っていた Cloudflare のアクセス解析スクリプトは公開前に削除済み（v1・final とも）
- Pages の比較表で 02・04 の final リンクが 404 だったため、02 は画像、04 は slides.pdf へのリンクに修正済み。公開サイトで16リンクすべて 200 を確認済み

## 記事関連のファイル
- `article/confluence-report.md`: Confluence 用の比較レポート本文（完成稿・FIXME 付き）← これを仕上げる
- `article/confluence-report-prompt.md`: 他の AI にレポートを書かせるためのプロンプト（データ一式入り）
- 各 `log.md`: 題材ごとの詳細な記録

## 残タスク（FIXME）
1. 全題材の見た目評価（◎○△）を記入し、結論と「用途別のおすすめ」（現在は仮案）を確定
2. スクリーンショットを貼る（テトリス3つ、キャラ3体、LP のファーストビュー PC/スマホ、表紙スライド3つ）
3. Genspark のスライド作成中に選択式の質問が出たかを確認して追記
4. Genspark の返答言語を確認して追記
5. Confluence に投稿（スペース・親ページは未定）
6. 補足: Claude のスライドは claude.ai の Artifact（非公開）なので、記事ではリポジトリの PDF を参照する
