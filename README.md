# LaTeX in Docker on VSCode

VSCode + Docker で LaTeX 環境を構築する．Latexmk を利用してソースをビルドしている．
執筆は "Remote - Containers" を利用してコンテナ内で行うことになる．

## Environment

テンプレート作成時の環境

- OS
  - Mac OS X 10.15.7 19H2
- Docker version 20.10.0, build 7287ab3
- Docker Compose version 1.27.4, build 40524192
- VSCode 1.52.1
- VSCode Extension
  - Remote - Containers v0.154.1

## Purpose

- LaTeX 環境構築の再現性を Docker で担保する
- VSCode extension "LaTeX Workshop" を利用して LaTeX の執筆を楽にする
  - linter
  - 数式のプレビュー

## 環境構築

1. このリポジトリの `Use this template` ボタンをクリックし，新しくリポジトリを作成する
2. 作成したリポジトリを clone：`git clone [GitHub repository URL]`
3. clone したリポジトリを VSCode で開く
4. cmd + shift + P で **"Remote-Containers: Reopen in Container"** を検索し実行すると，Docker コンテナのビルドが実行され，リモート環境を開いた状態でエディタが起動する．
5. LaTeX Workshop の設定：リンク先の [`settings.json`](https://gist.github.com/nukopy/ec870ac99ff27dd9f126cab7bf8e700d)（Gist）の設定をコピペする
6. プレビューを開く：`src/main.tex`（編集したいファイルで OK）を開いた状態にし，cmd + shift + P で **"LaTeX Workshop: View LaTeX PDF file"** を検索し実行すると，右ペインに PDF が表示される（エディタ右上の虫眼鏡ボタンを押してもプレビューを表示できる）．
7. 後は自由に LaTeX ソースを作成・編集するだけ