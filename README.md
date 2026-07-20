# AI Agent Workspace

Claude Code、Gemini CLI、Codex CLI、Antigravity CLI を同じ Dev Container で利用するための開発環境です。VS Code または Cursor でコンテナを起動すれば、各 CLI をすぐに使い始められます。

## 含まれる主なツール

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [Codex CLI](https://developers.openai.com/codex/cli/)
- Antigravity CLI（`agy`）
- Git、GitHub CLI（`gh`）、Docker CLI

コンテナは Node.js 20（Debian Bookworm）をベースにしています。

## 使い方

1. このリポジトリをクローンします。
2. VS Code または Cursor でリポジトリを開き、**Reopen in Container** を実行します。
3. コンテナの作成完了後、ターミナルで使いたい CLI を実行します。

```bash
claude
gemini
codex
agy
```

初回起動時は、各 CLI の案内に従ってテーマ設定や認証を行ってください。

## 設定の永続化

以下の設定ディレクトリは Docker の名前付きボリュームにマウントされるため、コンテナをリビルドしても認証情報や設定が保持されます。

- Claude Code: `/home/node/.claude`
- Gemini CLI: `/home/node/.gemini`
- Codex CLI: `/home/node/.codex`
- GitHub CLI: `/home/node/.config/gh`
- Google Cloud CLI: `/home/node/.config/gcloud`

認証をやり直したい場合は、対応する Docker ボリュームを削除してください。

## 任意の環境変数

コンテナ内の Git のユーザー情報は、`GIT_USER_NAME` と `GIT_USER_EMAIL` が設定されている場合に初回セットアップで自動設定されます。`.env` から環境変数を読み込む場合は、[`.devcontainer/devcontainer.json`](.devcontainer/devcontainer.json) の `runArgs` を有効にしてください。
