# LaTeX in Docker on VSCode

VSCode + Docker で LaTeX 環境を構築する．
ディストリビューションとして TeX Live 2020，LaTeX ソースのビルドツールとして Latexmk を利用している．また，VSCode 拡張の "Remote - Containers" を利用し，Docker コンテナ内でファイルの編集を行うことを前提としている．

以下の Docker イメージをベースとしている．

- Docker image
  - GitHub: [nukopy/ubuntu-texlive-ja](https://github.com/nukopy/ubuntu-texlive-ja)
  - Docker Hub: [nukopy/ubuntu-texlive-ja](https://hub.docker.com/repository/docker/nukopy/ubuntu-texlive-ja)

## Purpose

- Docker により，LaTeX の環境構築の再現性を担保する
- VSCode extension "LaTeX Workshop" を利用して LaTeX の執筆を楽にする
  - linter
  - 数式のプレビュー
  - latexindent による自動フォーマット

## Environment

テンプレート作成時の環境

- OS
  - Mac OS X 10.15.7 19H2
- Docker version 20.10.0, build 7287ab3
- Docker Compose version 1.27.4, build 40524192
- VSCode 1.52.1
- VSCode Extension
  - Remote - Containers v0.154.1
  - LaTeX Workshop v8.15.0

## Caution

本リポジトリの管理者は LaTeX のエコシステムに詳しいわけではない．
そのため，Docker イメージが必要以上に大きくなっていたり，LaTeX の設定ファイル等におかしな部分があったりする可能性がある．

ベースとなっている Docker イメージは正しく動くと思うが，それ以外の部分はあくまで管理者の手元の環境で動かすことを意図しているため，もしエラーが出た場合，それぞれの環境で設定ファイル等を調整すると良い．issue や PR は大歓迎です．

どうしても動かない場合，管理者が参考にした Docker イメージがいくつかあるので[そちら](https://github.com/nukopy/ubuntu-texlive-ja#cf)を参照してみると良い．

## Setup

0. Docker，Docker Compose，VSCode，VSCode 拡張の "Remote - Containers" をインストールする（各自ググってください）
1. 本リポジトリの `Use this template` ボタンをクリックし，新しくリポジトリを作成する
2. 作成したリポジトリを clone：`git clone [GitHub repository URL]`
3. clone したリポジトリを VSCode で開く
4. cmd + shift + P で **"Remote-Containers: Reopen in Container"** を検索し実行すると，Docker コンテナのビルドが実行され，リモート環境を開いた状態でエディタが起動する．
   - 別途パッケージが必要な場合，`.devcontainer/Dockerfile` を編集してからビルドする．
5. LaTeX Workshop の設定：リンク先の [`settings.json`](https://gist.github.com/nukopy/ec870ac99ff27dd9f126cab7bf8e700d#file-settings-json)（Gist）の設定をコピペする
   - このテンプレート内の `.latexmkrc` 用にリンク先の `settings.json` を書かれている
   - LaTeX ソースのビルドの設定（処理系など）を変更したい場合，`.latexmkrc` と VSCode の "LaTeX Workshop" の設定を変更する必要がある．場合によっては `.devcontainer/Dockerfile` を編集して処理系をインストールする必要がある場合もある
6. プレビューを開く：`src/main.tex`（編集したいファイルで OK）を開いた状態にし，cmd + shift + P で **"LaTeX Workshop: View LaTeX PDF file"** を検索し実行すると，右ペインに PDF が表示される（エディタ右上の虫眼鏡ボタンを押してもプレビューを表示できる）．
7. 後は自由に LaTeX ソースを作成・編集するだけ
