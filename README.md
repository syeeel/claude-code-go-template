# Go Development Template with Claude Code

Go言語開発用のDevContainer環境テンプレートです。

## 特徴

- **Go 1.23.2** - 最新の安定版Go
- **開発ツール完備**
  - `gopls` - Go Language Server（コード補完、リファクタリング）
  - `golangci-lint` - 統合リンター
  - `delve (dlv)` - デバッガー
  - `air` - ホットリロード
- **Claude Code統合** - AI支援による開発
- **VS Code拡張機能** - Go開発に最適化された設定

## セットアップ

### 1. Devcontainerの起動

VS Code / Cursorでこのプロジェクトを開き、コマンドパレットから：

```
Dev Containers: Rebuild and Reopen in Container
```

を実行してください。

### 2. 動作確認

コンテナが起動したら、以下のコマンドで環境を確認：

```bash
# Goのバージョン確認
go version

# 開発ツールの確認
gopls version
golangci-lint --version
dlv version
air -v
```

## 使い方

### 基本的な開発

```bash
# アプリケーションの実行
go run main.go

# ビルド
go build -o app

# テストの実行
go test ./...

# リンターの実行
golangci-lint run
```

### ホットリロード（Air使用）

```bash
# Airでホットリロードを有効にして開発
air

# .air.toml で設定をカスタマイズ可能
```

ファイルを保存すると自動的に再ビルド・再起動されます。

### デバッグ

VS Code / Cursorのデバッグ機能を使用するか、コマンドラインから：

```bash
# デバッガーを起動
dlv debug
```

## プロジェクト構成

```
.
├── .devcontainer/       # DevContainer設定
│   ├── Dockerfile       # Go開発環境の定義
│   └── devcontainer.json
├── .air.toml           # Airホットリロード設定
├── main.go             # メインアプリケーション
├── go.mod              # Go module定義
└── README.md           # このファイル
```

## サンプルアプリケーション

このテンプレートには簡単なHTTPサーバーが含まれています：

```bash
# サーバーを起動
go run main.go

# 別のターミナルで確認
curl http://localhost:8080
curl http://localhost:8080/health
```

## 開発環境の詳細

### インストール済みツール

- Go 1.23.2
- Node.js 20（Claude Code用）
- Git, GitHub CLI
- Zsh（デフォルトシェル）
- Git Delta（差分表示）

### Go開発ツール

- `gopls` - Language Server Protocol実装
- `golangci-lint` - 統合リンター（複数のリンターを統合）
- `delve` - Goデバッガー
- `air` - ライブリロードツール

### VS Code設定

- 保存時の自動フォーマット
- 保存時のインポート整理
- golangci-lintによる自動リント

## カスタマイズ

### Goバージョンの変更

`.devcontainer/Dockerfile` の `FROM golang:1.23.2-bookworm` を変更してください。

### 追加のGo依存関係

```bash
go get <package-name>
```

### 追加の開発ツール

`.devcontainer/Dockerfile` の該当セクションに追加してください。

## トラブルシューティング

### コンテナが起動しない

```bash
# コンテナを完全に再ビルド
Dev Containers: Rebuild Container Without Cache
```

### Go言語サーバーが動作しない

```bash
# goplsの再インストール
go install golang.org/x/tools/gopls@latest
```

## Claude Code について

このテンプレートはClaude Codeと統合されています。
詳しくは[公式ドキュメント](https://docs.anthropic.com/en/docs/claude-code/overview)をご覧ください。

## リンク

- [Go公式ドキュメント](https://go.dev/doc/)
- [Claude Code](https://claude.ai/code)
- [golangci-lint](https://golangci-lint.run/)
- [Air](https://github.com/air-verse/air)
