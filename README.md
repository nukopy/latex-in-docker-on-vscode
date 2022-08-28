# LaTeX in Docker on VSCode

Docker + Visual Studio Code で快適な LaTeX 環境を構築するリポジトリ

以下の Docker イメージをベースとしている。TeX Live 2022 を使用。

- Docker image
  - GitHub: [nukopy/ubuntu-texlive-ja](https://github.com/nukopy/ubuntu-texlive-ja)
  - Docker Hub: [nukopy/ubuntu-texlive-ja](https://hub.docker.com/repository/docker/nukopy/ubuntu-texlive-ja)

## このリポジトリの目的

- Docker / Docker Compose による煩雑な LaTeX 執筆環境構築の簡易化
- Latexmk による LaTeX のソースコードのビルド設定の簡易化
- VSCode extension "LaTeX Workshop" を利用した LaTeX 執筆環境の快適化
  - linter
  - latexindent による自動フォーマット
  - 数式のプレビュー

## 必要なソフトウェア

下記に列挙したソフトウェアを事前にインストールする必要があります。ソフトウェアは全て最新バージョンであることを前提としています。

- Docker
- Docker Compose
- Visual Studio Code (VSCode)
- VSCode Extensions
  - Remote - Containers
  - LaTeX Workshop

## Setup

1. 本リポジトリの `Use this template` ボタンをクリックし、新しくリポジトリを作成する
2. 作成したリポジトリを clone し、VSCode で開く

   ```sh
   git clone [Your Repository URL]
   cd [Your Repository Name]
   ```

3. cmd + shift + P（`Show All Commands` ショートカット）で **"Remote-Containers: Reopen in Container"** を検索し実行すると、Docker コンテナのビルドが実行され、リモート環境を開いた状態でエディタが起動する
   - 別途パッケージが必要な場合、`.devcontainer/Dockerfile` を編集してからビルドする
4. VSCode の `settings.json` を開き、[`config/settings.json`](./config/settings.json) の設定をコピペする
5. PDF プレビューを開く：`src/main.tex`（編集したいファイルで OK）を開いた状態にし、cmd + shift + P で **"LaTeX Workshop: View LaTeX PDF file"** を検索し実行すると、右ペインに PDF が表示される（エディタ右上の虫眼鏡ボタンを押してもプレビューを表示できる）。
6. 後は自由に LaTeX ソースを作成・編集するだけ。サンプルプロジェクトとして [`sample`](https://github.com/nukopy/latex-in-docker-on-vscode/tree/master/sample) ディレクトリ配下にドキュメント用プロジェクト、Beamer によるスライド用プロジェクトを用意してある、そちらをベースにするのも良い。
   - デフォルトのビルド設定では upLaTeX を処理系として使用している。これを変更する場合、`.latexmkrc` を編集する必要がある。場合によっては `Dockerfile` に処理系をインストールする処理を追加する必要がある。
