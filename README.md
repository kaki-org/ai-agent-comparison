# ai-agent-comparison

Cursor・Claude（Claude Code）・Genspark に同じプロンプトを渡し、成果物を比較する実験リポジトリです。

## 題材

| # | 題材 | プロンプト |
|---|------|------------|
| 01 | シンプルなテトリス | [prompts/01-tetris.md](prompts/01-tetris.md) |
| 02 | 柿のゆるキャラ画像 | [prompts/02-kaki-character.md](prompts/02-kaki-character.md) |
| 03 | ゆるキャラ紹介 LP（02 の自作キャラを使用） | [prompts/03-landing-page.md](prompts/03-landing-page.md) |
| 04 | 柿のスライド資料（02 の自作キャラを使用） | [prompts/04-slides.md](prompts/04-slides.md) |

## 実験ルール

- 全ツールに `prompts/` の同じプロンプトを渡す
- 一発目の出力を `v1/` に保存する
- 手直しは最大2回まで。最終版を `final/` に保存し、指示内容を `log.md` に記録する
- Cursor はデフォルトのモデル設定、Claude は Claude Code を使う
- Cursor / Claude Code は各題材ディレクトリを作業ディレクトリにし、他ツールの成果物を参照させない
- Claude Code は企画の文脈を持たない新規セッションで実行する
- Genspark の成果物はダウンロードして配置し、共有 URL を `log.md` に記録する
- 各ツールは筆者の普段の設定のまま使う（Claude Code は `~/.claude/CLAUDE.md`、Cursor は `~/AGENTS.md` を読み込む）
- 作業フォルダは他ツールの作業フォルダと同じ階層に置かない（Cursor が上位フォルダを検索して他ツールの成果物を読んだため。`cursor/03-landing-page/log.md` 参照）

## 評価

- 客観指標: 所要時間、手直し回数、そのまま動いたか、要件充足数
- 主観: 見た目を ◎○△ の3段階で筆者コメント
- 記事の最後に用途別のおすすめをまとめる

## 構成

```
prompts/                      全ツール共通のプロンプト
{cursor,claude,genspark}/
  {01-tetris,02-kaki-character,03-landing-page,04-slides}/
    v1/      一発目の出力
    final/   手直し後
    log.md   記録
article/draft.md              記事の下書き
index.html                    比較一覧（GitHub Pages）
```
