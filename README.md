# dotfiles

個人用のdotfiles管理リポジトリです。zsh、tmux、zellij、starship、miseなどの設定ファイルを一元管理します。

## 要件

- POSIX互換のシェル（sh, bash, zsh等）
- 対応OS: macOS
- Git

## インストール

```bash
git clone git@github.com:okkun510/dotfiles.git ~/ghq/github.com/okkun510/dotfiles
cd ~/ghq/github.com/okkun510/dotfiles
git checkout personal
sh init.sh
```

Homebrewのインストール、パッケージのインストール、dotfilesのリンク作成、miseランタイムのインストールまで自動で行います。初回実行時にGit設定（名前とメールアドレス）の入力を求められます。

### 初回セットアップ後の手動ステップ

1. GitHub CLIでSSH鍵を作成する
   ```sh
   gh auth login
   ```
2. ターミナルを再起動する（シェル設定やZinitプラグインの反映）
3. VSCodeやターミナルアプリにフォントを適用する

既存の設定ファイルがある場合は、事前にバックアップしてください（詳細は「既存ファイルがある場合」を参照）。

> **注意:** dotfiles の後に [enverter](https://github.com/okkun510/enverter) を実行してください。新しいPCのセットアップ手順の全体は enverter の README を参照してください。

## 管理している設定ファイル

- **zsh** (`.zshrc`) - シェル設定
- **tmux** - ターミナルマルチプレクサ設定
- **zellij** - モダンなターミナルワークスペース
- **starship** - クロスシェルプロンプト
- **mise** - ランタイムバージョンマネージャー
- **yazi** - ターミナルファイルマネージャー
- **SSH** - SSH設定
- **Homebrew** (`.Brewfile`) - パッケージ管理
- **gitmoji** - Gitコミット絵文字設定

## 使い方

### セットアップ
```sh
sh init.sh
```

### アンインストール
```sh
cd ~/dotfiles
stow -D -t "$HOME" src
```

### Dry-Run（実行内容の確認）
```sh
cd ~/dotfiles
stow -t "$HOME" --simulate -v src
```

## 既存ファイルがある場合

リンク先に通常のファイルやディレクトリが既に存在する場合、stowがコンフリクトを検出してエラーになります。既存ファイルを削除またはバックアップしてから再実行してください。

既存ファイルをリポジトリに取り込みたい場合は `stow --adopt` が使えます（詳細は `man stow` を参照）。

## テスト

```sh
sh init.test.sh
```

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。詳細は[LICENSE](LICENSE)ファイルを参照してください。