# marimo_tester
This is a project to test marimo notebook

## uv の使い方

uvはPython開発環境のオールインワンツール(らしい)

以下の機能を内包

 - 仮想環境
 - 依存関係
 - パッケージ管理

pip, venv, poetryのような機能をまとめてくれている(らしい)

しかも高速らしい。

### インストール方法

#### Mac, Linuxの場合

Curlでインストール可能

    curl -LsSf https://astral.sh/uv/install.sh | sh

バージョン確認は

    uv self version

実行すると

    uv 0.9.8 (85c5d3228 2025-11-07)

のような形でバージョンが出てくる

### 使い方

#### .gitignore

[こちら](.gitignore)を参照

GitHubのpythonデフォルトを使用

#### プロジェクトの初期化

このmarimo_tester内で以下を実行する

    uv init marimo_test_project

すると以下のようなディレクトリ構造となる
    .
    ├── LICENSE
    ├── marimo_test_project
    │   ├── main.py
    │   ├── pyproject.toml
    │   └── README.md
    └── README.md
    2 directories, 5 files

##### プロジェクトの中身

###### main.py

ただのサンプルコード

###### .python-version

Pythonのバージョン情報が保存

自分の環境では3.11が入っているからか、3.11になった(要調査)

###### pyproject.toml

```python
[project]
name = "marimo-test-project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.11"
dependencies = []
```

どうやらuv add などのコマンドでライブラリを足していくとdependenciesに追加されていくらしい

```python
[project]
name = "marimo-test-project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.11"
dependencies = [
    "marimo>=0.17.7",
    "matplotlib>=3.10.7",
    "numpy>=2.3.4",
    "pandas>=2.3.3",
]
```

#### 仮想環境構築

