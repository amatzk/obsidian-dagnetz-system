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

**4. 思い出す仕組み**
- グラフビューによる思考ネットワークの俯瞰
- キーワード・タグなどでインターネットのように検索
- 期間・属性などによるデータベースのような一覧表示
- AIによる意味的類似性を使った関連性の自動発見

**5. 脳の複製**
- **思考の追跡**：なぜその結論に至ったかの思考過程を記録
- **忘却しない第二の脳**：人間の記憶の限界を補完する外部記憶システム
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
    - 階層タグを使用禁止　フラットタグのみ
- ノート・添付ファイルの配置
    - 全てファイルは、作成日年月日ディレクトリ `01_data/YYYY/MM/DD/` 配下に配置
    - フォルダ階層による分類を一切行わない

**3. DAG構造の運用**
- 新規ノート作成時、関連する過去ノートへのリンクを積極的に作成
- 一つ以上のタグを必ず設定（ノートの孤立を防ぐため）
- ローカルグラフでノートや添付ファイルの関連性を確認

**4. 検索・一覧機能**
- **ローカルグラフ**：DAG構造の可視化
- **DataView**：期間・属性別自動ファイル・タスク一覧生成
- **Tag Folder**：タグベース一覧表示（実質的なMOC）
- **Floating Search**：キーワード・タグなど組み合わせ検索
- **Smart Connections** or **Similar Notes**：AIの意味的類似性を使った関連性の自動発見
- **Bases**：Vault内のファイルをデータベース化し、カスタム一覧表示

**5. 例外ルールと注意事項**
- 誤字・脱字の修正は過去ノートでも許可（Git履歴で追跡、修正しすぎ注意）
- 生成AIによるノート代筆は非推奨（自分の思考ではないため「第二の脳」の価値を損なう）

## ディレクトリの用途

- 00_template
    - テンプレート
    - [[01_note]]：新規ノート用
    - [[11_embed_code]]：Embed Code File プラグイン用
- 01_data/YYYY/MM/DD
    - マークダウン、添付ファイル、キャンバスなど全てのファイル置き場
    - 保管庫にファイルを追加する場合、追加した日付（YYYY/MM/DD）のディレクトリに全て入れる
    - 過去ファイルは編集禁止
    - ファイル名のリネームは許可
        - Obsidianの使い勝手から、ユニークなファイル名である必要があるため
- 02_view
    - DataView および Bases プラグインによる 一覧表示

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
    - 作成日時が自動挿入される（Templaterプラグイン）
2. **タイトル設定**:
    - トピックを簡潔に表す具体的なタイトルを付ける（F2）
    - 検索しやすい名前にする
    - 例: 「DAGネットワークの特徴」「量子コンピュータの基本原理」
3. **タグ設定**:
    -  一つ以上のタグを設定（ノートを孤立させないため）
    - 階層タグは使用禁止（複雑性回避）
    - 探しやすいタグをつける
    - タグが実質的なMOC（Map of Contents）として働く
        - Tag Folder で一覧表示
        - DataViewで一覧表示
4. **内容記述**:
    - トピックの概要・詳細を記述
    - 関連する既存ノートがあればリンクする
    - 引用や参考元があれば記録する
5. **書き終わったら編集禁止**:
    - 作成日内（寝るまで）に内容を完成させるのを推奨
    - 未完成でも、続きは別日に新規ノートとして作成する

**具体例**:
```
---
created: 2025-06-21 15:15:15
tags:
  - physics
  - quantum
---
## 量子ビットの概念

従来のコンピュータでは0か1の二値しか取れないビットを使用するが、量子コンピュータでは量子ビット（qubit）を使用する。量子ビットは0と1の重ね合わせ状態をとることができる。...
```

### Q2: 同じトピックについて日を跨いで書く場合は？

基本的にQ1と同じです。違いは以下。

**タイトル（ファイル名）が被らないようにを工夫する**
- 例えば「元のトピック名_YYYY-MM-DD」の形式を使用など
    - 例：「量子コンピュータの基本原理_2025-05-04」

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

1. **Floating Searchの活用**:
    - 検索画面からキーワードやタグなどを組み合わせて検索
    - 例: `tag:#quantum path:"2025/04"` で4月の量子関連ノートを検索
2. **Tag Folderによる閲覧**:
    - Tag Folderパネルでタグの一覧表示
    - 関連タグをクリックして関連ノートを素早く発見
3. **グラフビューの活用**:
    - ローカルグラフで関連ノートのDAG構造を視覚的に把握
    - ノート間の接続を確認し、知識の関連性を発見
4. **Basesによる一覧表示**:
    - vault内のデータをデータベースのように扱い、一覧表示やフィルタリングが可能
    - [[10_dashboard]]
        - 複数のBasesを埋め込んだダッシュボードノート
        - View：02_view配下の一覧表示用 `.md`や`.base`ファイルを一覧表示
        - Today | Pin：今日作成したファイルや、`Pin`タグを付与したファイルの一覧
        - Data：01_data配下の全てのファイル一覧
5. **Smart Connections or Similar Notesによる関連ノート一覧表示**
    - AIによる意味的類似性のあるノートの一覧表示
    - Smart ChatによるAIとの対話
6. **タスク管理**
    - [[20_tasks]]
        - タスク一覧のDataViewと、タスクが記載されたノートでフィルタしたBasesを埋め込みしてあるノート

### Q5: 過去のノートに誤字・脱字を見つけた場合は？

原則、過去ノートは編集禁止ですが、個人的に誤字・脱字に関しては編集をしてもよいと思います。Gitが編集履歴を保存しているので問題ないと思っています。柔軟に対応しましょう。編集しすぎないように注意！

### Q6: 生成AIにノートを書かせても良い？

やめたほうがいいです。**AIが書いた文章は「自分の思考」ではありません。**
このノート術は「忘却しない第二の脳」を構築するシステムです。AIに文章を書かせることは、この目標と根本的に矛盾します。
「思考の変遷を時系列で保存」と「過去の自分の振り返り」を実現するために、最終的な文章は必ず自分で執筆することを推奨します。

**適切な使い方**：
- **Smart Connections** or **Similar Notes**：意味的類似性による関連ノートの自動発見
- **アイデアの発想支援**：思考の出発点として活用（最終的には自分の言葉で再構築）
- **検索・整理の補助**：既存ノートの整理や関連性の発見

**避けるべき使い方**：
- ノートの内容をAIに代筆させる
- AI生成情報をそのまま記録する

## [Obsidian Web Clipper](https://obsidian.md/clipper) 用設定

```json
{
    "schemaVersion": "0.1.0",
    "name": "DAGnetz",
    "behavior": "create",
    "noteContentFormat": "",
    "properties": [
        {
            "name": "title",
            "value": "{{title}}",
            "type": "text"
        },
        {
            "name": "source",
            "value": "{{url}}",
            "type": "text"
        },
        {
            "name": "author",
            "value": "{{author|split:\\\", \\\"|wikilink|join}}",
            "type": "multitext"
        },
        {
            "name": "published",
            "value": "{{published}}",
            "type": "date"
        },
        {
            "name": "created",
            "value": "{{date|date:\\\"YYYY-MM-DD HH:mm:ss\\\"}}",
            "type": "date"
        },
        {
            "name": "description",
            "value": "{{description}}",
            "type": "text"
        },
        {
            "name": "tags",
            "value": "文献",
            "type": "multitext"
        }
    ],
    "triggers": [],
    "noteNameFormat": "{{title}}",
    "path": "01_data/{{date|date:YYYY/MM/DD}}"
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

デフォルトは、中国語フォントになっています。
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
    - Floating Search: Search Obsidian Globally (With Last State)
- Ctrl + Q
    - Git: Commit-and-sync and then close Obsidian
- Alt + H
    - Global Search and Replace: Seach and Replace in all files
- Alt + ↓
    - Outliner：Move list and sublists down
- Alt + ↑
    - Outliner：Move list and sublists up
- Alt + C
    - Templater: Insert 00_templates/11_embed_code.md
- Ctrl + R
    - ライブプレビュー/ソースモードを切り替える
- Ctrl + J
    - Templater: Create 00_templates/02_literature.md
- Alt + T
    - Minimal Theme Settings: Cycle between table width option

## [コアプラグイン](https://publish.obsidian.md/help-ja/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/%E3%82%B3%E3%82%A2%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3) 設定

使用するコアプラグインを選択します。

ONのコアプラグイン：

- Bases
- Footnotes view
- アウトゴーイングリンク
- アウトライン
- キャンバス
- クイックスイッチャー
- グラフビュー
- コマンドパレット
- バックリンク
- ファイルエクスプローラ
- ページビュー
- ワークスペース
- 検索

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

### [Dataview](https://github.com/blacksmithgu/obsidian-dataview)

Obsidian Vaultをクエリ可能なデータベースとして扱うプラグイン

ノートを俯瞰して一覧表示するために使用します。
02_view 配下に個人的に使う一覧表示を用意しています。
自分自身の用途に合わせてカスタムしてください。

Obsidian v1.9.10 リリースのBases機能により、タスク一覧を除く全てのDataViewを置き換えました。

- [[20_tasks]]
    - タグで絞り込みしたノートに記述されたタスクを全て一覧表示

- Enable JavaScript queries
    - ON

### [Embed Code File](https://github.com/almariah/embed-code-file)

ソースコードを埋め込むことができるプラグイン

別ファイルとしてコードを管理できるようになるので便利です。
自身の使用する言語を設定に追加してください。

### [Floating Search](https://github.com/Quorafind/Obsidian-Float-Search)

モーダルなど、大きい画面で検索画面が表示するプラグイン

Hotkey 設定：
- Floating Search: Search Obsidian Globally (With Last State) → Alt + F
    - Floating Search を最後の状態で開く

### [Git](https://github.com/Vinzent03/obsidian-git)

Gitで保管庫を管理するプラグイン

方針：
- mainブランチ1本
- コミットは手動で行う
    - Backup で一括操作
    - Backup = Staging → Commit → Pull → Push
- プッシュとプルは定期的に自動で行う
    - リポジトリの競合を可能な限り防ぐ
- Obsidianの起動時は自動的にプル
- Obsidianの終了方法はショートカット（Ctrl + Q）を使用
    - `Git: Create backup and close`
        - Backup
        - Obsidianを閉じる

デフォルトから変更した設定：

Automatic：
- Split automatic commit and push → ON
    - 自動コミットとプッシュを分割
- Vault commit interval (minites) → 0 (OFF)
    - 自動で`git commit`を行う周期
- Vault push interval (minutes) → 20
    - 自動で`git push`を行う周期
- Auto pull interval (minites) → 60
    - 自動で`git pull`を行う周期

Backup：
- Pull updates on startup → ON
    - Obsidian起動時に最新の変更を取得
- Push on backup → ON
    - バックアップをプッシュする
- Pull changes before push → ON
    - プッシュ前にプルを行う

Hotkey 設定：
- Git: Create backup and close → Ctrl + Q
    - バックアップの作成とObsidianの終了

### [Global Search and Replace](https://github.com/MahmoudFawzyKhalil/obsidian-global-search-and-replace)

Obsidian 保管庫内全てのファイルでグローバル検索と置換を実行するプラグイン

VSCodeの検索のように、横断検索して置換をするための機能になります。

Hotkey 設定：
- Global Search and Replace: Seach and Replace in all files → Alt + H
    - 全ファイルの検索と置換

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

### [Mononote](https://github.com/czottmann/obsidian-mononote)

各ノートがウィンドウペインごとに1つのタブのみを占有するようにするプラグイン

ノートが既に開いている場合は、現在のタブで同じファイルを開くのではなく、既存のタブにフォーカスが当てられます。リンク、メニュー、ホットキーからノートを開く場合に有効です。

Mononoteを正しく動作させるには、「設定」→「エディター」→「常に新しいタブにフォーカス」を必ず有効にする必要があります。（制作者談）

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

### [Slash Commander](https://github.com/alephpiece/obsidian-slash-commander)

Obsidian 用のカスタマイズ可能なスラッシュコマンドを追加するプラグイン

スラッシュコマンドを使えるようにする便利系プラグインです。
Embed Code File用のテンプレートをTemplaterに登録しているので、それをスラッシュコマンドで呼び出せるようにしています。
その他、コマンドパレットから呼び出せるコマンドは全て登録可能なので、お好きに設定してください。

### [Smart Connections](https://github.com/brianpetro/obsidian-smart-connections)

Smart ConnectionsはAIの意味的類似性を使ってObsidianのノート間の関連性を自動で発見し、手動でのリンク作成や整理の手間を省くプラグイン

Smart Connections
- Connections view
    - Exclude outlinks → ON
    - Hide blocks in results → ON
- Smart Environment
    - Excluded folders
        - 00_templates
        - 02_view

Smart Chat
- Chat
    - Language → 日本語

### [Similar Notes](https://github.com/joybro/obsidian-similar-notes)

AIの意味的類似性を使ってObsidianのノート間の関連性を自動で発見し、手動でのリンク作成や整理の手間を省くプラグイン
Smart Connectionsにおいて、Ollamaを使用するためには課金しなくてはならなくなったのに伴って導入した代替
Similar NotesとSmart Connectionsのどちらかを使う

Index：
- Exclude folders from indexing → 00_templates/ 02_view/
	- インデックスから除外するフォルダ
Display：
- Show similar notes at the bottom of notes → OFF
	- ノートの下部にSimilar Notesを表示

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

### [TagFolder](https://github.com/vrtmrz/obsidian-tagfolder)

タグをフォルダーのように表示するプラグイン

デフォルトから変更した設定：
- Behavior
    - Disable narrowing down → ON
        - 絞り込みの無効化。この機能を有効にすると、サブ構造を作る代わりに、関連するタグがタイトルとともに表示される。
        - 個人的に階層はフラットな方が好きなので……ここはお好きに切り替えてください。
- Filters
    - Target Folders
        - 01_data
            - 00_templatesと02_viewを除くため

### [Templater](https://github.com/SilentVoid13/Templater)

Templaterプラグインは、テンプレート言語を定義しています。
それによって、変数や関数の結果をノートに挿入することができます。
また、それらの変数や関数を操作するJavaScriptコードを実行することもできます。

デフォルトから変更した設定：

- Template folder location → 00_templates
    - テンプレートフォルダの場所
- Trigger Templater on new file creation → ON
    - 新規ファイル作成でTemplaterをトリガーするか

Template hotkeys
- 00_templates/[[11_embed_code]].md
    - [[11_embed_code]]は、Embed Code File プラグインのコード埋め込みテンプレート
    - Hotkey設定：
        - Templater: Insert 00_templates/[[11_embed_code]].md → Alt + C
- 00_templates/[[02_literature]].md
    - 文献ノート用テンプレート
    - Hotkey設定：
        - Templater: Create 00_templates/[[02_literature]].md → Ctrl + J

Folder templates
- / ... 00_templates/[[01_note]].md
    - 保管庫配下に、新規ノートを作成したときに適応するテンプレートの設定

### [Various Complements](https://github.com/tadashi-aikawa/obsidian-various-complements-plugin)

IDEの自動補完のように単語を補完するプラグイン

「\[\[」と入力すること無く内部リンクを貼ることができるのですごく便利です。
フロントマターやカスタム辞書、保管庫内を参照し文字列補間、現在のファイル内で文字列補間など多機能なので好みで調整してください。→ [ドキュメント](https://tadashi-aikawa.github.io/docs-obsidian-various-complements-plugin/)

デフォルトから変更した設定：

- Main
    - Strategy
        - Japanese
    - Match Strategy
        - partial
- Current file complements
    - Enable Current file complements → OFF
- Internal link complement
    - Exclude self internal link → ON
