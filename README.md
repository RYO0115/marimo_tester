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


### .gitignore

[こちら](.gitignore)を参照

GitHubのpythonデフォルトを使用

### プロジェクトの初期化

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

#### プロジェクトの中身

##### main.py

ただのサンプルコード

##### .python-version

Pythonのバージョン情報が保存

自分の環境では3.11が入っているからか、3.11になった(要調査)

##### pyproject.toml

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

### 依存関係

#### 依存関係の更新 (lock)

uvで作成した依存関係(ライブラリのバージョン)を更新するコマンド

    uv lock

#### 依存関係の確認

ライブラリのバージョンを確認

    uv tree

    marimo-test-project v0.1.0
    ├── marimo v0.17.7
    │   ├── click v8.3.0
    │   ├── docutils v0.22.3
    │   ├── itsdangerous v2.2.0
    │   ├── jedi v0.19.2
    │   │   └── parso v0.8.5
    │   ├── loro v1.8.2
    │   ├── markdown v3.10
    │   ├── msgspec-m v0.19.2
    │   ├── narwhals v2.10.2
    │   ├── packaging v25.0
    │   ├── psutil v7.1.3
    │   ├── pygments v2.19.2
    │   ├── pymdown-extensions v10.16.1
    │   │   ├── markdown v3.10
    │   │   └── pyyaml v6.0.3
    │   ├── pyyaml v6.0.3
    │   ├── starlette v0.50.0
    │   │   ├── anyio v4.11.0
    │   │   │   ├── idna v3.11
    │   │   │   ├── sniffio v1.3.1
    │   │   │   └── typing-extensions v4.15.0
    │   │   └── typing-extensions v4.15.0
    │   ├── tomlkit v0.13.3
    │   ├── uvicorn v0.38.0
    │   │   ├── click v8.3.0
    │   │   └── h11 v0.16.0
    │   └── websockets v15.0.1
    ├── matplotlib v3.10.7
    │   ├── contourpy v1.3.3
    │   │   └── numpy v2.3.4
    │   ├── cycler v0.12.1
    │   ├── fonttools v4.60.1
    │   ├── kiwisolver v1.4.9
    │   ├── numpy v2.3.4
    │   ├── packaging v25.0
    │   ├── pillow v12.0.0
    │   ├── pyparsing v3.2.5
    │   └── python-dateutil v2.9.0.post0
    │       └── six v1.17.0
    ├── numpy v2.3.4
    └── pandas v2.3.3
        ├── numpy v2.3.4
        ├── python-dateutil v2.9.0.post0 (*)
        ├── pytz v2025.2
        └── tzdata v2025.2
    (*) Package tree already displayed

### 仮想環境構築

#### 仮想環境で使用するpythonのインストール

    uv python install 3.10 3.11

#### インストール済みのpython一覧取得

    uv python list


#### この環境で使うPythonを固定する

デフォルト3.11だった場合に3.13に変更する

    uv python pin 3.13

出力は以下の通り
    Updated `.python-version` from `3.11` -> `3.13`

### CLIツール

#### インストール

    uv tool install ruff

#### インストール済みtoolの一覧表示

    uv tool list

### uvx (一時環境での実行)

#### (例) pytestを一時的に実行

    uvx pytest

#### オプション

|オプション|説明|
|:-------|:---|
|--from|指定パッケージのコマンドを使用|
|--with|指定パッケージも同時にインストールして実行|
|--isolated|完全に新しい一時環境(すでに構築された環境に依存しない)で実行|

    uvx --with pytest pytest test_sample.py




