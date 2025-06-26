---
title: "Gemini CLIを使って記事を公開する"
emoji: "🤖"
type: "tech"
topics: ["cli", "gemini", "google", "zenn"]
published: false
---

# Gemini CLIを使って記事を公開する

この記事では、Googleの提供する`gemini-cli`を用いて、Zennの記事を作成し公開するまでの手順を解説します。

## 1. Gemini CLIの導入

まずは、`gemini-cli`を自身の開発環境に導入します。

### インストール

`gemini-cli`はnpmパッケージとして提供されています。以下のコマンドでグローバルにインストールします。

```bash
npm install -g @google/gemini-cli
```

### APIキーの設定

次に、Gemini APIを利用するためのAPIキーを設定します。
APIキーは [Google AI Studio](https://aistudio.google.com/app/apikey) から取得できます。

取得したAPIキーを環境変数に設定します。

```bash
export GEMINI_API_KEY="YOUR_API_KEY"
```

`.bashrc`や`.zshrc`に追記しておくと便利です。

## 2. Gemini CLIを使ってZennの記事を公開する

`gemini-cli`の準備が整ったら、次はZennの記事を作成していきます。

### Zennリポジトリの準備

まず、Zennのコンテンツを管理するためのリポジトリを準備します。
`zenn-cli`を使って初期化しましょう。

```bash
npx zenn-cli init
```

### 記事の作成

次に、`gemini`コマンドに依頼して、記事の雛形を作成してもらいます。
今回は「Gemini CLIを使って記事を公開する」というテーマで記事を作成します。

```bash
gemini "「Gemini CLIを使って記事を公開する」というタイトルのZenn記事を作成してください。記事のスラッグは`gemini-cli-publish`とします。"
```

上記のコマンドを実行すると、`gemini`が記事の内容を生成し、`articles/gemini-cli-publish.md`というファイルに保存してくれます。

### 内容の確認と修正

`gemini`が生成した記事は、必ずしも完璧ではありません。
生成された`articles/gemini-cli-publish.md`を開き、内容を確認・修正します。

特に、技術的な正確性や、自身の文体に合っているかなどをチェックしましょう。

### Zennへのデプロイ

記事の準備ができたら、Zennにデプロイします。
以下のコマンドを実行すると、GitHubリポジトリと連携しているZennのコンテンツが更新されます。

```bash
npx zenn-cli deploy
```

これで、Gemini CLIを使ったZennの記事公開は完了です。

## まとめ

本記事では、`gemini-cli`を導入し、Zennの記事を作成・公開するまでの一連の流れを解説しました。
AIを活用することで、記事執筆の効率を大幅に向上させることができます。ぜひ試してみてください。
