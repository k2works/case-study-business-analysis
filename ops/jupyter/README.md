# Python環境構築とファイルセットアップ手順

このドキュメントでは、Python環境の構築から、A社事例分析に必要なファイルセットアップまでの手順を説明します。

## 1. Python環境の構築

### 1.1 pyenvのインストール
- Windowsの場合、[pyenv-win](https://github.com/pyenv-win/pyenv-win)を使用します。
- 以下のコマンドを実行してインストールしてください。

```bash
pip install pyenv-win --user
```

### 1.2 Pythonバージョンのインストール
- 必要なPythonバージョンをインストールします。

```bash
pyenv install 3.x.x  # 必要なバージョンを指定
pyenv global 3.x.x   # グローバルで使用するバージョンを設定
```

### 1.3 仮想環境の作成
- `pyenv-virtualenv`を使用して仮想環境を作成します。

```bash
pyenv virtualenv 3.x.x case4_env  # "case4_env"は仮想環境の名前
pyenv activate case4_env          # 仮想環境を有効化
```

### 1.4 必要なライブラリのインストール
- 必要なPythonライブラリをインストールします。

```bash
pip install pdfplumber python-docx pytesseract pillow pdf2image
```

## 2. ファイルセットアップ

### 2.1 テキスト抽出スクリプトの準備
- `extract_text_from_files.ipynb`を使用して、PDFやWordファイルからテキストを抽出します。
- 文字化けを防ぐために、`pdfplumber`を使用したコードを実装済みです。

### 2.2 Markdownファイルの作成
- 抽出したテキストを基に、以下のMarkdownファイルを作成します。
  - `PLBS.md`: 連結貸借対照表（BS）と連結損益計算書（PL）を記載
  - `case4_setup.md`: 分析作業のワークフローを記載

### 2.3 PlantUMLによるワークフロー図の作成
- `case4_setup.md`にPlantUML形式でワークフローを記述しています。
- 必要に応じて、PlantUML対応ツールで図を生成してください。

## 3. 実行手順

1. 仮想環境を有効化します。

```bash
pyenv activate case4_env
```

2. Jupyter Notebookを起動し、`extract_text_from_files.ipynb`を実行します。

```bash
jupyter notebook
```

3. 抽出したテキストを基に、`PLBS.md`や`case4_setup.md`を編集・確認します。

4. 必要に応じて、PlantUMLでワークフロー図を生成します。

## 4. 注意事項
- 仮想環境を終了する際は、以下のコマンドを実行してください。

```bash
pyenv deactivate
```

- 必要なPythonライブラリが不足している場合は、適宜`pip install`で追加してください。