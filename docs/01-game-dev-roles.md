# ゲーム開発に必要な役割（調査結果）

Steam でゲームを1本出すまでに、業界では何をどう分担しているのか。
まず「業界標準の役割マップ」を整理し、次に「個人開発＋AI での現実的な圧縮版」に落とす。

---

## 1. 業界標準の役割マップ

ゲーム開発の職能は、大きく **設計 / 実装 / アート / 音 / 進行 / 品質 / 事業** の7領域に分かれる。

### 1-1. 設計（Design）

| 役割 | 責務 | 主な成果物 |
|---|---|---|
| ゲームデザイナー | コアメカニクス、システム、ルール、成長・進行、難易度曲線 | GDD（Game Design Document）、システム仕様、バランス表 |
| レベルデザイナー | ステージ／マップ構成、プレイヤー導線、難易度配置 | レベルレイアウト、プレイフロー図 |
| ナラティブデザイナー | 世界観、ストーリー、キャラクター、セリフ | 設定資料、シナリオ、テキストリソース |
| UI/UX デザイナー | メニュー、HUD、操作フロー、可読性、アクセシビリティ | 画面遷移図、ワイヤーフレーム、UI仕様 |

設計の本質は「作るものを決めて、決めたことを文書として固定する」こと。
個人開発で最も飛ばされがちで、最も後で効いてくる領域。

### 1-2. 実装（Engineering）

| 役割 | 責務 |
|---|---|
| ゲームプレイプログラマ | 設計された仕様をコードにする。プレイヤー挙動、敵AI、システム |
| エンジンプログラマ | 描画・物理・メモリなど基盤層（既製エンジン利用なら不要に近い） |
| ツールプログラマ | エディタ拡張、データ入稿ツール、自動化 |
| テクニカルアーティスト | アートと実装の橋渡し。シェーダ、最適化、アセット取り込み規約 |
| ビルド／リリースエンジニア | ビルド自動化、CI、プラットフォーム入稿（Steam depot 等） |

### 1-3. アート（Art）

アートディレクター（画作りの統一方針）／コンセプトアーティスト／2D・3Dモデラー／アニメーター／VFXアーティスト／UIアーティスト。
個人開発では「自分で描く」「アセットストアで買う」「外注する」「生成AIを使う」の4択で、
どれを選んでも **アートディレクション（統一方針）だけは誰かが持つ必要がある**。

### 1-4. 音（Audio）

作曲（BGM）／サウンドデザイン（SE）／オーディオ実装（ミキシング、トリガー配線）。
規模が小さいほど1人が兼ねるが、「音の実装」はプログラマ側の仕事として残りやすい。

### 1-5. 進行（Production）

プロデューサー／プロジェクトマネージャ。
**スケジュール・スコープ・優先順位**に対する決定権を持つ。各分野の創作判断はしないが、
「これは今回のリリースに入れない」を言う役割。個人開発で最も欠けやすいのがこれ。

### 1-6. 品質（QA）

テスト計画の作成と実行、バグの再現手順の記録、修正の検証（リグレッション確認）。
加えて **プレイテスト**（第三者に遊ばせて観察する）は、開発者自身では絶対に代替できない。

### 1-7. 事業・パブリッシング（Business）

| 役割 | 責務 |
|---|---|
| マーケティング／PR | ストアページの訴求、トレーラー、プレス・配信者対応、ウィッシュリスト獲得 |
| コミュニティマネージャ | Discord・SNS・Steam掲示板での対話、フィードバック回収 |
| プラットフォーム担当 | Steamworks の設定、審査対応、ビルド入稿、リリース日管理 |
| ローカライズ | 多言語対応、文字数・フォント・文化的調整 |
| 法務・レーティング | 利用規約、権利処理、年齢レーティング、素材ライセンス確認 |

---

## 2. Steam 固有で必ず発生する作業

「ゲームが完成した ≠ Steam で売れる」。以下は**開発とは別工数**として必ず積む。

- **Steam Direct 手数料**: 1タイトルあたり 100 USD（買い切り、条件を満たすと後で回収可能）
- **ストアページ審査**: 完成したページを "Mark as ready for review" して申請。通常 **3〜5営業日**。
  修正差し戻しを見込み、公開希望日の **7営業日以上前**に出す
- **「近日公開（Coming Soon）」ページ**: リリースの **最低2週間前**から公開されている必要がある
  （実際にはウィッシュリストを積むため、数ヶ月前から出すのが定石）
- **ビルド審査**: ストアページ審査が通ってからビルドを提出する（順序が決まっている）
- **必要な提出物**: ストア用アートワーク各サイズ、スクリーンショット、トレーラー、
  説明文、タグ、システム要件、対応言語表記、年齢レーティング情報、depot/ビルド構成

出典: [Release Process](https://partner.steamgames.com/doc/store/releasing) /
[Review Process](https://partner.steamgames.com/doc/store/review_process) /
[Coming Soon](https://partner.steamgames.com/doc/store/coming_soon)

---

## 3. 個人開発（あなた＋AI）への圧縮

上の20以上の役割を全部持つのは不可能。**兼務してよいもの／絶対に分けるべきもの**で切る。

### 3-1. 圧縮後の10役割

| # | 圧縮後の役割 | 元の職能 | 個人開発での実態 |
|---|---|---|---|
| 1 | **プロデューサー** | プロデューサー／PM | あなた本人。スコープを削る決定をする |
| 2 | **ゲームデザイナー** | ゲーム／レベルデザイン | GDD を書き、仕様を固定する |
| 3 | **ナラティブ／テキスト** | ナラティブ、ローカライズ原稿 | ゲーム内文言をすべて管理 |
| 4 | **UI/UX** | UI/UX、UIアート | 画面遷移とわかりやすさ |
| 5 | **ゲームプレイ実装** | 各種プログラマ | エンジン上での実装の中核 |
| 6 | **テクニカルアート／パイプライン** | TA、ツール | アセット規約、命名、最適化 |
| 7 | **アートディレクション** | AD、各種アーティスト | 方針決定 ＋ 制作は自作/購入/外注/生成AI |
| 8 | **オーディオ** | 作曲、SE、実装 | 音の一覧と実装仕様。素材は購入/生成が現実的 |
| 9 | **QA** | QA、プレイテスト | 自動テスト＋自分のテスト＋**他人のプレイテスト** |
| 10 | **リリース／マーケ** | ビルド、Steamworks、PR、コミュニティ | Steam 入稿とウィッシュリスト獲得 |

### 3-2. 「まず1本出す」ための優先順位

調査で一貫していたのは **「スコープが個人開発を殺す。技術力ではなく」** という点。
`Buckshot Roulette`（メカニクス1つ、Godot、800万本）のような例が示すとおり、
最初の1本では次の順で投資する。

1. **プロデューサー（スコープ管理）** ← ここが崩れると他が全部無駄になる
2. **ゲームデザイナー＋ゲームプレイ実装** ← 面白さの本体
3. **QA（特に他人のプレイテスト）** ← 独りよがりの検出
4. **リリース／マーケ** ← 出さなければ0本
5. アート・オーディオ・UI ← 「統一されていること」＞「上手いこと」
6. ナラティブ・ローカライズ ← 初作では最小限でよい

### 3-3. エンジン選定が役割設計に効く（重要）

**Godot を推奨する。**理由は初心者向けだからではなく、**AI エージェントと相性が良いから**。

- Godot のシーン（`.tscn`）・リソース（`.tres`）・スクリプト（`.gd`）はすべて**テキスト形式**。
  → Claude が直接読み書きでき、差分レビューでき、Git で衝突解決できる
- Unity のプレハブ／シーンは実質バイナリ寄りで、エージェントによる編集・レビューが困難
  → 実装エージェントの担当範囲が「C#スクリプトだけ」に狭まる
- Godot 本体 120MB、ライセンス費ゼロ、2D の初動が速い

Unity を選ぶ場合、後述のサブエージェント設計は**そのまま使えるが、
「エディタ上での手作業」があなた側に多く残る**前提で読むこと。

> **前提の明示**: 以下のサブエージェント設計は「Godot / 2D / 個人開発 / Steam PC リリース」を
> 想定して書いている。エンジンやジャンルを変える場合、影響するのは主に
> `gameplay-engineer` と `tech-artist` の2つで、他の役割はほぼそのまま流用できる。

---

## 出典

- [Game Development Team Roles & Responsibilities (Guide) — Tono Game Consultants](https://tonogameconsultants.com/game-development-disciplines/)
- [What Are the Job Roles in the Game Development Industry? — FutureLearn](https://www.futurelearn.com/info/courses/introduction-to-indie-games/0/steps/96373)
- [Building the Dream Game Development Team — Negative Five Ventures](https://negativefive.vc/game-startup/building-the-dream-game-development-team-essential-roles-in-an-indie-game-studio/)
- [Game Development Team Roles and Responsibilities — Video Game Development Authority](https://videogamedevelopmentauthority.com/game-development-team-roles)
- [Roles in game development — iLogos Game Studios](https://ilogos.biz/roles-in-game-development/)
- [Game Audio Glossary: Game Development Roles — A Sound Effect](https://www.asoundeffect.com/game-audio-glossary-development-roles/)
- [Release Process — Steamworks](https://partner.steamgames.com/doc/store/releasing)
- [Review Process — Steamworks](https://partner.steamgames.com/doc/store/review_process)
- [Coming Soon — Steamworks](https://partner.steamgames.com/doc/store/coming_soon)
- [Best Tools & Game Engines for Solo Indie Developers (2026) — Ziva](https://ziva.sh/blogs/solo-game-development)
- [Godot vs Unity in 2026 — DEV Community](https://dev.to/linou518/godot-vs-unity-in-2026-which-engine-should-indie-developers-choose-50g4)
