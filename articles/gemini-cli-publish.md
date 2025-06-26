---
title: "Gemini CLIを使って記事を公開する"
emoji: "🤖"
type: "tech"
topics: ["cli", "gemini", "google", "zenn"]
published: true
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

### Zennへの公開

記事の準備ができたら、Zennに公開します。ZennはGitHubリポジトリと連携してコンテンツを公開するため、以下の手順でGitHubにプッシュします。

1.  **Gitリポジトリの初期化とコミット**
    まだGitリポジトリでない場合は初期化し、変更をコミットします。

    ```bash
    git init
    git add .
    git commit -m "feat: Zenn記事の追加"
    ```

2.  **GitHubリポジトリの作成と連携**
    GitHubで新しいリポジトリを作成し、ローカルリポジトリと連携させます。

    ```bash
    git remote add origin <GitHubリポジトリのURL>
    git branch -M main
    git push -u origin main
    ```
    `<GitHubリポジトリのURL>` は、ご自身のGitHubリポジトリのURLに置き換えてください。

3.  **ZennとGitHubの連携設定**
    Zennのダッシュボードにアクセスし、以下の手順でGitHubリポジトリを連携設定します。

    -   Zennにログイン後、[ダッシュボード](https://zenn.dev/dashboard)へ移動します。
    -   左サイドバーの「GitHub連携」をクリックします。
    -   「新しいリポジトリを連携する」ボタンをクリックし、連携したいGitHubリポジトリを選択します。
    -   連携が完了すると、選択したリポジトリの`main`ブランチにプッシュするたびにZennのコンテンツが自動的に更新され、記事が公開されます。

    詳細な設定方法は、[Zenn公式ドキュメント](https://zenn.dev/zenn/articles/connect-to-github)もご参照ください。

これで、Gemini CLIを使って作成したZennの記事が公開されます。

## まとめ

本記事では、`gemini-cli`を導入し、Zennの記事を作成・公開するまでの一連の流れを解説しました。
AIを活用することで、記事執筆の効率を大幅に向上させることができます。ぜひ試してみてください。
