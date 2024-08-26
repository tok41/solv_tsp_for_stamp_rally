# スタンプラリー対策！

スタンプラリーの経路探索をする。

## アプローチ

[TODO]現状1種類のアプローチだが、今後複数の手法を試行する上で、ディレクトリ構造などを工夫する

- 駅をノード、駅間の経路をエッジとしたグラフを構成
    - 直接接続がある駅間にエッジを構成
    - エッジのコストはその区間の運賃とする
- 単純な巡回セールスマン問題として経路を探索する
    - スタート駅を指定し戻ってくる経路を計算
    - 1日で周れる駅数などは現状考慮してない
    - ゴール駅は現状考慮してない

### 参考

- [巡回セールスマン問題(OR-Toolsガイド)](https://developers.google.com/optimization/routing/tsp?hl=ja)

## 環境構築

### 事前準備(推奨)

- [pyenv](https://github.com/pyenv/pyenv#installation)の導入
- pyenvを通して適当なバージョンのpythonをインストールしておく

### 環境構築手順

venvの環境を作る。`kasou`は仮想環境の名称なので、なんでも良い。

```bash
python -m venv kasou
```

仮想環境を有効化

```bash
source kasou/bin/activate
```

仮想環境で必要なパッケージのインストール

```bash
python -m pip install -r requirements.txt 
```

jupyter labの起動。
直接jupyterコマンドを実行しても良いが、下記のシェルスクリプトでjupyterlabのポートを環境変数`JUPYTER_PORT`から取得して設定する。

```bash
bash bin/run_jupyter.sh
JUPYTER_PORT=48888 bash bin/run_jupyter.sh
```

仮想環境の終了

```bash
deactivate
```
