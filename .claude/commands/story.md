# コマンド: 執筆・添削・反映

「第N話」を執筆・添削・反映するための標準ワークフローを実施します。
TODOリストツールを使いましょう。

## Phase 1 — 下書き（story-writer）

- 役割: `story-writer` エージェントが第N話の下書きを作成する。
- 成果物: `episodes/NNN.txt`
- ステップ:
  - 1. エージェントを実行する前に成果物ファイル `episodes/NNN.txt` の存在を確認
  - 2. ファイルが存在しない場合、`story-writer` エージェントを実行して下書きを作成

## Phase 2 — 添削（story-editor）

- 役割: `story-editor` エージェントで添削・評価・校正を行う。
- 成果物: `episodes/NNN-fix.md`

## Phase 3 — 修正反映 & 再コミット

- 役割: `story-fixer` エージェントで添削を反映して本文を修正しコミットする。
- 注意: 修正箇所がなくなるまでphase 2〜5を繰り返す。

## Phase 4 — 空行の調整
- 役割: `episode-formatting-adjuster` エージェントで空行の調整を行う。

## Phase 5 — 最終確認
- 役割: `story-editor` エージェントで最終確認を行う。
- 注意: 修正箇所がなくなるまでphase 3から繰り返す。

## Phase 6 — 大幅改稿が必要な場合
- 判定: `story-editor` が「大幅改稿」を推奨した場合。
- 対応: ファイルを削除し、`story-writer` に再度執筆を依頼して Phase1 からやり直す。

この手順に従えば、執筆→添削→反映のサイクルを安定して回せます。
