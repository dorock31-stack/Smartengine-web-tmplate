# SmartEngine Claude Code Skill｜導入用最終版

SmartEngineのWeb制作工程をClaude Codeで再利用するためのプロジェクト用Skillです。

## 収録内容

- `.claude/skills/build-smartengine-websites/SKILL.md`：SmartEngine共通の制作手順
- `.claude/skills/build-smartengine-websites/references/`：工程・業種・プラン別の参照資料
- `.claude/skills/build-smartengine-websites/templates/`：A・B工程のテンプレート
- `CLAUDE.md`：案件固有情報の記入場所
- `docs/`：案件の成果物を置く場所
- `src/`：C工程の実装ファイルを置く場所

## 推奨：案件ごとに導入する

1. ZIPを解凍する。
2. 解凍したフォルダの中身を、制作案件のルートへコピーする。
3. `CLAUDE.md`へ案件名、業種、プラン、現在工程などを記入する。
4. ターミナルで案件フォルダへ移動する。
5. `claude`を実行する。
6. Claude Code内で `/build-smartengine-websites` を実行するか、通常文で工程を指示する。

既存案件へ入れる場合は、`.claude`、`CLAUDE.md`、`docs`を案件ルートへコピーしてください。既存の`CLAUDE.md`がある場合は上書きせず、内容を統合してください。

## 全案件で使う：ユーザー共通Skillとして導入する

Skillフォルダだけを、ユーザー共通のSkill置き場へコピーします。

コピー元：

```text
.claude/skills/build-smartengine-websites/
```

コピー先：

```text
~/.claude/skills/build-smartengine-websites/
```

Windows PowerShellでは、通常次の場所です。

```text
$HOME\.claude\skills\build-smartengine-websites\
```

この方式ではSkillは全案件で使えます。ただし、案件固有の情報は各案件ルートの`CLAUDE.md`へ記入してください。

## 起動確認

Claude Codeを案件ルートで起動し、次を実行します。

```text
/context
```

`CLAUDE.md`がMemory filesに表示されれば、案件ルールが読み込まれています。

次に、以下のどちらかでSkillを呼び出します。

```text
/build-smartengine-websites
```

または：

```text
SmartEngineの制作手順に従って、現在の資料を確認し、A工程だけ進めてください。
```

## 基本ワークフロー

### 1. 案件情報を記入

`CLAUDE.md`に以下を記入します。

- 案件名
- 顧客名
- サイト種別
- 業種
- 対象エリア
- 契約プラン
- 現在工程
- 参考URL
- 固有ルール
- 技術構成

### 2. A工程

```text
/build-smartengine-websites
現在ある顧客資料とURLを確認し、A工程だけ進めてください。
docs/ANALYSIS_TEMPLATE.mdを基にdocs/ANALYSIS.mdを作成してください。
次工程には進まないでください。
```

### 3. B工程：内容

```text
承認済みのdocs/ANALYSIS.mdを基に、B工程のコンテンツ設計だけ進めてください。
docs/CONTENTS_TEMPLATE.mdを基にdocs/CONTENTS.mdを作成してください。
見た目の設計には進まないでください。
```

### 4. B工程：デザイン

```text
承認済みのdocs/ANALYSIS.mdとdocs/CONTENTS.mdを基に、ビジュアル設計を進めてください。
docs/DESIGN_TEMPLATE.mdを基にdocs/DESIGN.mdを作成してください。
CONTENTS.mdの文章は変更しないでください。
```

### 5. C工程

```text
承認済みのdocs/CONTENTS.mdとdocs/DESIGN.mdを正として、C工程を進めてください。
src配下へHTML、CSS、JavaScriptを分離して実装してください。
スマホ表示、日本語改行、CTA、アクセシビリティも確認してください。
```

## ファイルの役割

- `CLAUDE.md`：その案件で常に守るルール
- `SKILL.md`：必要なときに呼び出すSmartEngine共通工程
- `ANALYSIS.md`：誰に、何を、どの順番で伝えるか
- `CONTENTS.md`：実際に掲載する文章、構成、リンク、画像指定
- `DESIGN.md`：配色、書体、写真、レイアウト、動き、レスポンシブ仕様
- `src/`：実装物

## 注意

- `.claude`は隠しフォルダです。Windowsのエクスプローラーで見えない場合は「表示」から隠しファイルを有効にしてください。
- 既存の`.claude`フォルダがある場合はフォルダごと上書きせず、`skills/build-smartengine-websites`を追加してください。
- 既存の`CLAUDE.md`がある場合は上書きしないでください。
- Claude CodeがSkillを認識しない場合は、一度セッションを終了して案件ルートから再起動してください。
