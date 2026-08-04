# Windowsでの取り入れ方

## 事前準備

Claude Codeをまだ導入していない場合は、Node.js 18以降とGit for Windows、またはWSLを準備します。

```powershell
npm install -g @anthropic-ai/claude-code
claude doctor
```

## 案件ごとに導入する方法

例として案件フォルダが次の場合：

```text
C:\Users\ユーザー名\Documents\案件名
```

1. ZIPを解凍する。
2. 解凍フォルダ内の以下を案件フォルダへコピーする。

```text
.claude
CLAUDE.md
docs
src
```

3. PowerShellを案件フォルダで開く。

```powershell
cd "C:\Users\ユーザー名\Documents\案件名"
claude
```

4. Claude Code内で確認する。

```text
/context
/build-smartengine-websites
```

## 全案件で共通利用する方法

解凍したSkillをユーザー共通領域へコピーします。

```powershell
$source = ".\.claude\skills\build-smartengine-websites"
$destination = "$HOME\.claude\skills\build-smartengine-websites"
New-Item -ItemType Directory -Force -Path "$destination" | Out-Null
Copy-Item "$source\*" "$destination" -Recurse -Force
```

その後、Claude Codeを再起動します。

案件固有情報は、各案件のルートに置く`CLAUDE.md`で管理してください。
