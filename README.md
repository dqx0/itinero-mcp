# Itinero MCP

[itinero](https://trip.dqx0.com/) の旅程・持ち物・タスク・支払いを、普段使うAIから扱うための接続設定です。
itineroのアカウント登録、Glenへのログイン、APIキーは不要です。利用するAIサービスの契約や利用条件は別途必要です。

## Codex

```sh
codex plugin marketplace add dqx0/itinero-mcp
codex plugin add itinero@itinero-mcp
```

Codexで新しいセッションを開始し、`/mcp` でitineroのツールが表示されることを確認してください。

## Claude Code

```sh
claude plugin marketplace add dqx0/itinero-mcp
claude plugin install itinero@itinero-mcp
```

Claude Codeを再起動し、`/mcp` で接続を確認してください。

## Cursor

`~/.cursor/mcp.json` の `mcpServers` に次の設定を追加します。既存のサーバー設定は残してください。

```json
{
  "mcpServers": {
    "itinero": {
      "type": "http",
      "url": "https://trip.dqx0.com/mcp"
    }
  }
}
```

CursorのMCP設定からitineroを有効にします。

## VS Code / GitHub Copilot

コマンドパレットの **MCP: Add Server** から **HTTP** を選択します。
URLは `https://trip.dqx0.com/mcp`、名前は `itinero` にします。
サーバーを信頼して開始し、**MCP: List Servers** で接続を確認してください。

## ChatGPT

カスタムMCPアプリを利用できるプラン・ワークスペースの場合、Web版の設定でDeveloper modeを有効にします。
アプリの作成画面でURLに `https://trip.dqx0.com/mcp`、認証方式に **なし（None）** を指定し、ツールを確認して作成します。
新しいチャットで作成したアプリを選びます。利用範囲はプランや管理者設定によって異なります。

## 使い始める

itineroで旅を開き、共有URLと相談内容をAIに渡してください。

> この旅程を読んで、時間が詰まりすぎているところを教えて。

> 2日目の予定を整理して。保存する前に変更内容を見せて。

旅のURLを知っている人は、ブラウザからもAIからも閲覧・編集・削除できます。URLは一緒に旅をする人や利用するAIにだけ共有してください。
既存の旅を一覧から探す機能はありません。対象の旅のURLが必要です。旅の新規作成はAIからもできます。
変更は内容を確認してから許可してください。削除ツールには明示的な確認が必要です。

## 以前のプラグインから切り替える

旧 `itinero@itinero` を無効にしてから、このリポジトリの `itinero@itinero-mcp` を追加してください。
手動で同じ接続先を登録していた場合も、一方だけを有効にしてください。
Glenの認証画面が出る場合は、古い接続設定が残っていないか確認し、AIアプリで新しいセッションを開始してください。

アクセスが集中した場合は、しばらく待ってから再試行してください。MCPの429応答では `Retry-After` に待ち時間を返します。

## このリポジトリについて

接続用プラグインと導入手順のみを公開しています。サービス本体のソースコードや利用者の旅程データは含みません。
MCPはHTTP（Streamable HTTP）で提供しています。プラグインを使わず、対応クライアントにURLを直接登録することもできます。

## 公式ガイド

- [Codex plugins](https://developers.openai.com/codex/plugins)
- [Claude Code plugins](https://code.claude.com/docs/en/discover-plugins)
- [Cursor MCP](https://cursor.com/docs/mcp)
- [VS Code MCP](https://code.visualstudio.com/docs/agent-customization/mcp-servers)
- [ChatGPT Developer mode](https://help.openai.com/en/articles/12584461)

[プライバシー](https://trip.dqx0.com/privacy) · [利用規約](https://trip.dqx0.com/terms)
