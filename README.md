# MLflow AI Gateway サンプル

## 概要

MLflow AI Gatewayは、以下のようなLLM開発における共通の課題を解決するためのライブラリです。

- APIトークンを利用することによるセキュリティの問題
- APIの過度な利用によるコストの問題
- APIキー管理におけるガバナンスの問題

このレポジトリでは、MLflow AI Gatewayを使用して、特定のモデルプロバイダ（例：OpenAI、Anthropicなど）に対して、リクエストを実行する方法を示します。

## 項目

- MLflow AI Gatewayのセットアップ
- ルートの設定とデプロイメント
- Fluent APIによるリクエスト

## 前提条件

- MLflow 2.5

## 実行方法

1. MLflow AI Gatewayの起動

    ``` bash
    mlflow gateway start --config-path config.yaml --port 5000 --host 0.0.0.0 --workers 1
    ```

2. APIドキュメントの確認

    [APIドキュメント](http://localhost:5000/docs)にアクセス

3. Fluent APIによるリクエスト

``` python
from mlflow.gateway import query, set_gateway_uri

set_gateway_uri(gateway_uri="http://localhost:5000")

response = query(
    "chat",
    {"messages": [{"role": "user", "content": "What is the best day of the week?"}]},
)

print(response)

```


## 参考

- [MLflow ドキュメント](https://mlflow.org/docs/latest/gateway/index.html)
- [MLflow AI Gatewayの発表
強力なLLMアーキテクチャとインターフェースツールの提供](https://www.databricks.com/jp/blog/announcing-mlflow-ai-gateway)