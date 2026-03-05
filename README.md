# obsidian-dagnetz-system

> [!IMPORTANT]
> このREADMEは、自分のリポジトリを作成したときに削除してください。

## 構想

思考の変遷を時系列で記録し、過去の自分を振り返ることで創造的思考を生み出すシステム

![dagnez-image](01_data/2025/06/21/sample.svg)

**1. 編集制限ルール**
- 編集制限の基準
    - 編集可能：最長ノート作成日の睡眠前まで
    - 編集禁止：一度睡眠を取った後は未来永劫凍結
- 制限の理由
    - 睡眠により脳の記憶整理（刈り込み）が発生し忘却・記憶の捏造をしてしまう
    - 睡眠前の純粋な思考状態をノートに保存し、思考の変遷を完全記録

**2. 分類禁止ルール**
- 階層構造の排除
    - 分類による階層構造（木構造）の構築を一切禁止
    - 階層タグの使用禁止（フラットタグのみ許可）
- ファイルの固定配置
    - 全ファイルを作成日ディレクトリ（YYYY/MM/DD）配下に配置
    - 内容による分類を行わず、時系列のみで物理的整理
- 禁止の理由
    - 意味的な整合性が破綻した際、再構成作業を完全回避
    - 「分類の迷い」という認知負荷の排除

**3. 時系列単調性DAG**
- 自動形成の仕組み
    - 編集制限ルール：新しいノートから古いノートへの一方向リンクのみが可能
    - 分類禁止ルール：時系列での固定配置が知識の時間軸を保証
- 形成される構造
    - 有向非循環グラフ（Directed Acyclic Graph）の自然な形成
    - 循環参照のない、過去から未来への一方向ネットワーク
    - 思考の変遷を時系列で追跡可能

**4. 繋げる仕組み**
- AIによる意味的に関連するノートの一覧表示から、リンクをノートへ貼り付け

**5. 思い出す仕組み**
- Dashboardでノートを一覧表示
- AIによる意味的に関連するノートの発見
- キーワード・タグなどでインターネットのように検索
- グラフビューによる思考ネットワークの俯瞰

**6. 第二の脳**
- **思考の追跡**：なぜその結論に至ったかの思考過程を記録
- **忘却しないもう一つの脳**：人間の記憶の限界を補完する外部記憶システム
- **思いがけない発見**：過去の知識と現在の問題の偶発的組み合わせによる新たな洞察

## シンプルな運用

**1. 編集制限の運用**
- 全ファイル共通
    - ユニークなファイル名維持のためリネームは許可
- ノート（マークダウン .md ファイル）
    - デフォルトをリーディングビューにして誤編集を防止
    - 後日、続きを書く場合は新規ノートを作成し、過去ノートにリンク
    - プロパティのタグ、タスクのチェック の2つのみ後日編集可能
- 添付ファイル（.md ファイルを除く全てのファイル）
    - 画像、コード、キャンバスなど、ノートを除く全てが対象
    - 過去のファイルの編集は、作成日年月日ディレクトリ `01_data/YYYY/MM/DD/` 配下にコピーし編集

**2. 分類禁止の運用**
- タグ
    - ノートへのアクセス効率向上のための道標が目的
    - 全てのノートに対しデフォルトのタグを付与
	    - note タグ → 通常ノート（00_templates/01_note.md）
	    - task タグ → タスクノート（00_templates/02_task.md）
	    - clip タグ → Web Clipper によって生成されたタグ
	- 特殊タグ
		- pin タグ → 固定表示するノート
		- dashboard → ダッシュボード専用
    - 階層タグを使用禁止　フラットタグのみ
- ノート・添付ファイルの配置
    - 全てファイルは、作成日年月日ディレクトリ `01_data/YYYY/MM/DD/` 配下に自動配置
    - フォルダ階層による分類を一切行わない

**3. DAG構造の構築
- AIによる意味的類似性のあるノート一覧から、関連があるもののリンクを貼る

**4. 例外と注意事項**
- 誤字・脱字の修正は過去ノートでも許可（Git履歴で追跡、修正しすぎ注意）
- 生成AIによるノート代筆は非推奨（自分の思考ではないため「第二の脳」の価値を損なう）

## ディレクトリの用途

- 00_template
    - テンプレート置き場
    - 01_note：新規ノート
    - 02_task：タスクノート
- 01_data/YYYY/MM/DD
    - マークダウン、添付ファイル、キャンバスなど全てのファイル置き場
    - 保管庫にファイルを追加する場合、追加した日付（YYYY/MM/DD）のディレクトリに全て入れる
    - 昨日以前の全てのファイルは編集禁止
    - ファイル名のリネームは許可
        - Obsidianの使い勝手から、ユニークなファイル名である必要があるため
- 02_view
    - Dashboardノート

## テンプレートの使い方

> [!WARNING]
> このテンプレートを使用する際は、必ずプライベートリポジトリとして設定してください。個人情報や機密データの保護は利用者の責任となります。公開リポジトリでの使用は推奨されません。

「Use this template」から新規リポジトリを作成した場合は、不要なファイルが含まれているので削除しコミットしてください。

削除対象の不要なファイルおよびディレクトリ：
- README.md
- LICENSE
- 01_data/2025/06/21/SampleNote.md
- 01_data/2025/06/21/sample.drawio
- 01_data/2025/06/21/sample.svg

## 実践的QA

### Q1: 新しいトピックについて書く場合は？

新しいトピックについてノートを作成する場合のワークフローは以下の通り。

1. **ノート作成**:
    - 新規ノートを作成（Ctrl + N）
    - 自動的に「01_data/YYYY/MM/DD/」ディレクトリに保存される（Templaterプラグイン）
2. **タイトル設定**:
    - トピックを簡潔に表す、検索しやすい具体的なタイトルを付ける（F2）
    - 例: 「DAGネットワークの特徴」「量子コンピュータの基本原理」
3. **タグ設定**:
    - note タグは自動で付与される（01_note テンプレート）
    - 必要であればタグを設定（Dashboardでの視認性のため）
    - 階層タグは使用禁止（複雑性回避）
4. **内容記述**:
    - 内容：トピックの概要・詳細を記述
    - 情報源：引用や参考元があれば記録する
    - 内部リンク：関連する既存ノートがあればリンクする
    - 上記3つより多くの見出しを作ることになるならば、粒度が大きいと判断して別のノートを作成することを推奨
5. **書き終わったら編集禁止**:
    - 作成日内（寝るまで）に内容を完成させるのを推奨
    - 未完成でも、続きは別日に新規ノートとして作成する

**具体例**:
```md
---
tags:
  - note
  - physics
---
## 1. thoughts

量子ビットの概念

従来のコンピュータでは0か1の二値しか取れないビットを使用するが、量子コンピュータでは量子ビット（qubit）を使用する。量子ビットは0と1の重ね合わせ状態をとることができる。...

## 2. source
[タイトル](URL)

## 3. related link
[[関連ノート]]
```

### Q2: 同じトピックについて日を跨いで書く場合は？

基本的にQ1と同じです。違いは以下。

**タイトル（ファイル名）が被らないようにを工夫する**
- 例えば「YYYY-MM-DD_元のトピック名」の形式を使用など
    - 例：「2025-05-04_量子コンピュータの基本原理」

**リンク構造**
- 冒頭で前回ノートへの明示的なリンクや埋め込みを作成
    - 例：`「前回の\[\[量子コンピュータの基本原理]]の続きとして...」`

### Q3: 添付ファイル（画像、図表、コードなど）を編集する場合は？

添付ファイルも知識の一部として扱い、ノートと同様の編集制限を適用します。

1. **編集禁止**
    - 添付ファイル（画像、コード等）も過去のものは編集禁止
    - 過去ノートとの整合性を維持するために重要

2. **編集が必要な場合の対応**
    - 過去の添付ファイルをコピーして、今日の日付のディレクトリ（01_data/YYYY/MM/DD/）に貼り付け
    - コピーした添付ファイルを編集
    - 新しいノートから新しい添付ファイルへリンク

3. **ファイル名の付け方を工夫する**
    - 例えば、オリジナルファイル名に日付を追加する
        - 例：「量子アルゴリズム図_2025-05-01.png」→「量子アルゴリズム図_2025-05-03.png」

### Q4: 検索と一覧について具体的な方法は？

以下の方法で過去の知識を効率的に検索・活用できます。

1. **Omnisearchの活用**:
    - 検索画面からキーワードやタグなどを組み合わせて検索
2. **Basesによる一覧表示**:
    - vault内のファイルをデータベースのように扱い、一覧表示やフィルタリングが可能
    - 10_dashboard
        - 複数のBasesを埋め込んだダッシュボード
        - Task：taskタグを付与したファイルの一覧
        - Pin：`Pin`タグを付与したファイルの一覧
        - Today：今日作成したファイルの一覧
        - Data：01_data配下の全てのファイル一覧
3. **AIによる関連ノート一覧表示**
    - ノート間で意味的類似性のあるノートの一覧表示

### Q5: 過去のノートに誤字・脱字を見つけた場合は？

原則、過去ノートは編集禁止ですが、個人的に誤字・脱字に関しては編集をしてもよいと思います。Gitが編集履歴を保存しているので問題ないと思っています。柔軟に対応しましょう。編集しすぎないように注意！

### Q6: 生成AIにノートを書かせても良い？

やめたほうがいいです。**AIが書いた文章は「自分の思考」ではありません。**
このノート術は、自分の脳の外部に存在する「忘却しない第二の脳」を構築するシステムです。生成AIに書かせたこと文章をは、自分自身の脳にはない情報となります。
どうしても生成AIの文章を保存したいならば、更に自分の言葉で書き直すことを推奨します。そうすれば、自分の脳に記憶の爪痕を残すことができると考えられます。

**適切な使い方**：
- **ノート間の意味的類似性の算出**：AIによる関連ノートの自動発見
- **アイデアの発想支援**：思考の出発点として活用（最終的には自分の言葉で再構築）
- **検索・整理の補助**：既存ノートの整理や関連性の発見

**避けるべき使い方**：
- ノートの内容をAIに全て代筆させる
- AI生成情報をそのまま記録する

## [Obsidian Web Clipper](https://obsidian.md/clipper) 用設定

```json
{
	"schemaVersion": "0.1.0",
	"name": "DAGnetz",
	"behavior": "create",
	"noteContentFormat": "## 1.content\n\n## 2.sources\n\ntitle:{{title}}\nurl:{{url}}\npublished:{{published}}\n\n## 3.links",
	"properties": [
		{
			"name": "tags",
			"value": "clip",
			"type": "multitext"
		}
	],
	"triggers": [],
	"noteNameFormat": "{{date|date:YYYY-MM-DD}}_{{domain}}_{{title}}",
	"path": "01_data/{{date|date:\"YYYY/MM/DD\"}}"
}
```

## Obsidian 設定

[ここからはじめる - Obsidian 日本語ヘルプ - Obsidian Publish](https://publish.obsidian.md/help-ja/%E3%81%93%E3%81%93%E3%81%8B%E3%82%89%E3%81%AF%E3%81%98%E3%82%81%E3%82%8B)
デフォルト設定から変更している部分を記載します。

### エディタ

- 新規タブのデフォルトビュー
    - リーディングビュー

### ファイルとリンク

- 内部リンクを毎回更新する
    - ON
- 新規ノートの作成場所
    - 以下で指定されたフォルダ
- 新規ノートを作成するフォルダ
    - 01_data
- 新規添付ファイルの作成場所
    - 現在のファイルと同じフォルダ
- すべてのファイル拡張子を認識
    - ON

### 外観

テーマ
- [Minimal](https://github.com/kepano/obsidian-minimal)
#### フォント

デフォルトは、中国語のようなよくわからないにフォントになっています。
自分好みの日本語フォントを設定するとよいでしょう。
ここでは [M+ FONTS](https://mplusfonts.github.io) を設定しています。

- インターフェースフォント
    - M PLUS 1
- テキストフォント
    - M PLUS 1
- モノスペースフォント
    - M PLUS 1 Code

#### インターフェース

タブタイトルバーでファイル名が編集できるけれど、ファイル内でも編集できるので不要だと判断しました。
ヘッダーのメニューは使いません。機能はコマンドパレットから使います。

- タブタイトルバーを表示
    - OFF

### ホットキー

ユーザによる割り当て：

- Alt + F
    - Omnisearch: Vault search
- Ctrl + Q
    - Git: Commit-and-sync and then close Obsidian
- Alt + H
    - Global Search and Replace: Seach and Replace in all files
- Alt + ↓
    - Outliner：Move list and sublists down
- Alt + ↑
    - Outliner：Move list and sublists up
- Ctrl + R
    - ライブプレビュー/ソースモードを切り替える
- Ctrl + M
    - Templater: Create 00_templates/02_task.md
- Alt + T
    - Minimal Theme Settings: Cycle between table width option

## [コアプラグイン](https://publish.obsidian.md/help-ja/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/%E3%82%B3%E3%82%A2%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3) 設定

使用するコアプラグインを選択します。

ONのコアプラグイン：

- Bases
- グラフビュー
- コマンドパレット
- ファイルエクスプローラ
- ページビュー
- ワークスペース

## コミュニティプラグイン 設定

### [Auto Link Title](https://github.com/zolrath/obsidian-auto-link-title)

URLを貼ったら、自動的にウェブページを取得してリンクタイトルを抽出し、正しいタイトルが設定されたマークダウンリンクを作成するプラグイン

設定の変更なし

### [Colored Tags](https://github.com/pfrankov/obsidian-colored-tags)

タグに色付けをするプラグイン

デフォルト設定のままでいいけれど、個人的には以下の設定にしています。

- Palette
    - Custom
- Custom palette

ライト：

```
fce8e8-e8fcfc-eefce8-f3e8fc-fcf7e8-e8eefc-e8fcf3-fce8f7-fcf0e8-e8f7fc-edfce8-f7e8fc-fcfce8-e8edfc-e8fcf7-fce8ed
```

ダーク：

```
7a1010-107a7a-407a10-40107a-7a5510-10407a-107a40-7a1055-7a3810-105d7a-1d7a10-5d107a-747a10-1f107a-107a5d-7a102a
```

### [Git](https://github.com/Vinzent03/obsidian-git)

Gitで保管庫を管理するプラグイン

方針：
- mainブランチ1本
- コミットは手動で行う
    - Commit-and-sync で一括操作
    - Commit-and-sync = Staging → Commit → Pull → Push
- プッシュとプルは定期的に自動で行う
    - リポジトリの競合を可能な限り防ぐ
- Obsidianの起動時は自動的にプル
- Obsidianの終了方法はショートカット（Ctrl + Q）を使用
    - `Git: Commit-and-sync and then close Obsidian`
        - Commit-and-sync
        - Obsidianを閉じる

デフォルトから変更した設定：

Automatic：
- Auto commit-and-sync interval (minites) → 0 (OFF: Default)
    - 自動で`commit-and-sync`を行う周期
    - 自身の使い方に合わせて変更してください
- Auto commit-and-sync after stopping file edits → ON
	- 編集を止めてからX分後に`commit-and-sync`を行う
	- 上記、interval設定が有効のとき動作します

Commit message：
- List filenames affected by commit in the commit body → ON
	- コミットメッセージの本文（Body）に、どのファイルが変更されたかのリストを自動で含めます

Pull：
- Pull on startup → ON
	- Obsidian起動時にPullをする

Miscellaneous：
- Diff view style → Unified
	- 差分ビューの表示方式
- Show status bar → OFF
	- ステータスバーの表示
- Show branch status bar → OFF
	- ブランチの表示
	- main ブランチ一本運用のため不要

Hotkey 設定：
- Git: Create backup and close → Ctrl + Q
    - バックアップの作成とObsidianの終了

### [Image Toolkit](https://github.com/sissilab/obsidian-image-toolkit)

画像をクリックするとポップアップ表示され、プレビュー、ズーム、移動、回転、反転、反転、コピーなどの操作ができるプラグイン

設定の変更なし

### [Minimal Theme Settings](https://github.com/kepano/obsidian-minimal-settings)

Minimal Theme 付属のプラグイン
Obsidianの設定パネルからテーマをカスタマイズすることができます。

デフォルトから変更した設定：
- フォントサイズの設定はご自由に

Features：
- Underline internal links → OFF
    - 内部リンクに下線を引く
- Maximize media → OFF
    - 画像と動画を行幅分埋める

Typography：

- Text font size → 16
    - テキストのフォントサイズ
- Small font size → 13
    - 小さいフォントサイズ
- Line height → 2
    - 行の高さ
- Normal line witdh → 40
    - 通常の行の幅

### [Omnisearch](https://github.com/scambier/obsidian-omnisearch)

Obsidianの標準検索を大幅に強化するコミュニティプラグイン

Hotkey 設定：
- Omnisearch: Vault search → Alt + F

Behavior：
- Folders to downrank in search results → 00_templates, 00_view
	- 指定フォルダ内のファイルを検索結果の下位に表示

User Interface
- Show embed references → 0
	- 埋め込みの表示

### [Outliner](https://github.com/vslinko/obsidian-outliner)

WorkflowyやRoamResearchのようなリストの操作感にするためのプラグイン

個人的に、VSCodeと同じような操作感にするために入れています。
- Alt + ↑ でリストを上に移動
- Alt + ↓ でリストを下に移動

Outliner 設定：
- Stick the cursor to the content → Stick cursor out of bullets and checkboxes
    - カーソルをコンテンツに固定 → カーソルを箇条書きやチェックボックスの外に固定
- Enhance the Tab key → OFF
    - Tabキーの機能拡張
- Enhance the Enter key → OFF
    - Enterキーの機能拡張
- Enhance the Ctrl+A or Cmd+A behavior → ON
    - Ctrl+AまたはCmd+Aの動作拡張
- Improve the style of your lists → OFF
    - リストのスタイル改善
- Draw vertical indentation lines → OFF
    - 垂直インデントラインの描画
- Vertical indentation line click action → Toggle Folding
    - 垂直インデントラインクリック時の動作 → 折りたたみの切り替え
- Drag-and-Drop → ON
    - ドラッグアンドドロップ
- Debug mode → ON
    - デバッグモード

Hotkey 設定：
- Outliner：Move list and sublists down → Alt + ↓
    - アウトライナー：リストとサブリストを下に移動
- Outliner：Move list and sublists up → Alt + ↑
    - アウトライナー：リストとサブリストを上に移動

### [Style Settings](https://github.com/mgmeyers/obsidian-style-settings)

スニペット、テーマ、プラグインのCSSファイルで設定オプションのセットを定義することができるプラグイン

デフォルトから変更した設定：
- フォントサイズの設定はご自由に

Minimal → Headings → Level 1 Headings：
- H1 font size → 2em
    - H1のフォントサイズ

Minimal → Headings → Level 2 Headings：
- H2 font size → 1.6em
    - H2のフォントサイズ
- H2 divider line → ON
    - H2の区切り線

Minimal → Headings → Level 3 Headings：
- H3 font size → 1.4em
    - H3のフォントサイズ
- H3 divider line → ON
    - H3の区切り線

Minimal → Headings → Level 4 Headings：
- H4 font size → 1.2em
    - H4のフォントサイズ
- H4 divider line → ON
    - H4の区切り線

Minimal → Properties：
- Hide properties heading → ON
    - プロパティの見出しを隠す
- Hide "Add property" button → ON
    - "プロパティの追加"ボタンを隠す

Minimal → Sidebars：
- Hide help button → ON
    - ヘルプボタンを隠す

### [Templater](https://github.com/SilentVoid13/Templater)

Templaterプラグインは、テンプレート言語を定義しています。
それによって、変数や関数の結果をノートに挿入することができます。
また、それらの変数や関数を操作するJavaScriptコードを実行することもできます。

デフォルトから変更した設定：

- Template folder location → 00_templates
    - テンプレートフォルダの場所
- Trigger Templater on new file creation → ON
    - 新規ファイル作成でTemplaterをトリガーするか

- 00_templates/02_task.md
    - タスクノート用テンプレート
    - Hotkey設定：
        - Templater: Create 00_templates/02_task.md → Ctrl + M

Folder templates
- / ... 00_templates/01_note.md
    - 保管庫配下に、新規ノートを作成したときに適応するテンプレートの設定
