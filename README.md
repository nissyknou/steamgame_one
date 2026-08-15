# 『合図（あいず）』 / *Signal*（仮題）

**疎遠になった二人の友人が、共有した記憶を新しい順に遡っていく、2人協力必須のパズルゲーム。**
遡るほどに、二人は互いを必要とするようになる。

二人は分割画面の別々の場所にいて、**互いのためにしか動けない**。
自分の行く手を塞ぐものは、相手にしか取り除けない。

| | |
|---|---|
| ジャンル | 2人協力必須パズル・アドベンチャー |
| テーマ | 友情 |
| プレイ時間 | 1〜2時間 |
| プレイ人数 | 2人（同一画面ローカル協力 + Steam Remote Play Together） |
| エンジン | Godot 4.x |
| プラットフォーム | Steam / PC |

---

## ドキュメント

| ファイル | 内容 |
|---|---|
| [CLAUDE.md](CLAUDE.md) | **全エージェント共通の前提**。技術スタック、スコープ境界、通信規約、コーディング規約 |
| [docs/GDD.md](docs/GDD.md) | **憲法**。コンセプト、協力メカニクス、章構成、スコープ定義 |
| [docs/specs/coop-mechanic.md](docs/specs/coop-mechanic.md) | 協力メカニクス（分割画面＋交差操作）の実装仕様 |
| [docs/01-game-dev-roles.md](docs/01-game-dev-roles.md) | ゲーム開発に必要な役割の調査。Steam 固有の作業、個人開発向けの圧縮版 |
| [docs/02-subagent-design.md](docs/02-subagent-design.md) | 役割をサブエージェントへ落とし込む設計方針 |
| [docs/03-scope-management.md](docs/03-scope-management.md) | なぜスコープが個人開発を殺すのか。全判断の土台 |

## サブエージェント

| エージェント | 役割 | 状態 |
|---|---|---|
| [`game-design-reviewer`](.claude/agents/game-design-reviewer.md) | 設計整合性・スコープ番犬（read-only） | ✅ 稼働 |
| `gameplay-engineer` | ゲームプレイ実装 | フェーズ1で作成 |
| `qa-engineer` | テスト実行・バグ再現 | フェーズ1で作成 |
| `ux-designer` / `art-director` / `audio-director` / `narrative-writer` | — | フェーズ3で作成 |
| `steam-release-manager` / `marketing-researcher` | — | フェーズ3〜4で作成 |

導入順序の根拠は [docs/02-subagent-design.md](docs/02-subagent-design.md) §6。

## 進捗

| フェーズ | ゴール | 状態 |
|---|---|---|
| **0** | 企画確定（GDD + CLAUDE.md） | ✅ 完了 |
| **1** | **面白さの検証** — 部屋3室の縦切りプロトタイプ | ⬜ 次はここ |
| 2 | 全14〜16室のグレーボックス通しプレイ | ⬜ |
| 3 | アート・音・UI・テキスト | ⬜ |
| 4 | Steam リリース | ⬜ |

> フェーズ1が最重要。ここで「2人が喋らない」なら企画ごと作り直す。
> 絵も音も物語も、コアが検証されるまで一切作らない。
