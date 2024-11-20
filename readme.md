# ml-llm (My Little LLM)

個人で手軽に使える、プライバシー重視のLLMベースチャットボット

## 概要

My Little LLM（ml-llm）は、1つのHTMLファイルで動作する軽量なチャットボットフロントエンドです。
ローカル環境やLAN内で動作するLarge Language Model（例：Gemma 2 2B）と組み合わせることで、
プライバシーを保ちながら手軽に利用できるチャットボットを実現します。

## 特徴

- **シンプルな構成**: 単一のHTMLファイルで完結し、複雑なセットアップは不要
- **プライバシー重視**: チャット履歴を永続的に保存しないため、機密情報の管理が容易
- **柔軟なセッション管理**: 必要に応じてチャットセッションの保存・復元が可能

## 必要要件

- モダンなWebブラウザ（Chrome, Firefox, Safari等の最新版）
- LLMサーバー（以下のいずれか）
  - [MLX LM server](https://github.com/ml-explore/mlx-examples/blob/main/llms/mlx_lm/SERVER.md) + [日本語版Gemma 2 2B](https://developers-jp.googleblog.com/2024/10/gemma-2-for-japan.html)
  - その他OpenAI ChatCompletion互換性のあるLLMチャットサーバー

## インストール方法（おすすめ）

1. LLMサーバーのセットアップ（別途手順を参照）

2. フロントエンドを起動

https://muojp.github.io/ml-llm/ をWebブラウザで開く

## インストール方法（セルフホストしたい場合）

1. このリポジトリをクローン、もしくはZIPファイルとしてダウンロード
```bash
git clone https://github.com/muojp/ml-llm.git
```

2. LLMサーバーのセットアップ（別途手順を参照）

3. フロントエンドを起動

index.htmlをWebブラウザで開く

## 基本的な使い方

1. フロントエンドを起動
2. LLMサーバーのエンドポイントURLを設定
3. チャットを開始

## セッション管理

### 過去発言の改変
- 自分の発言欄をダブルクリックすると内容を編集して再度結果を生成する

### セッションの保存
- チャット欄に「DUMP」と入力して送信すると当該セッションの履歴をJSONで出力するので、任意の場所へコピペ

### セッションの復元
- チャット欄に「 `RESTORE:{...}` 」と保存したJSONを貼り付けて送信すると履歴を復元

## LLMサーバーのセットアップ

```bash
pip install mlx-lm
mlx_lm.server --model mlx-community/gemma-2-2b-jpn-it-8bit --host 0.0.0.0
```

## セキュリティ上の注意

- このアプリケーションは個人利用を想定しています
- 機密情報を扱う場合は、必ずローカル環境またはセキュアなLAN内、VPN経由のアクセス、適切な証明書運用と組み合わせたTLS環境整備など適切に経路の安全性を確保して使用してください
- `mlx-lm.server` のデフォルト実装の公開サーバーでの運用は推奨されません

## ライセンス

BSD-2-Clause license

## トラブルシューティング

よくある問題と解決方法：

1. LLMサーバーに接続できない
   - サーバーが起動していることを確認
   - URLとポート番号が正しいか確認
   - ファイアウォールの設定を確認

2. レスポンスが遅い
   - サーバーのリソース使用状況を確認

## サポート

- GitHubのIssueで報告してください

## 謝辞

- MLXチームの皆様
- MLX-LMチームの皆様
- Gemmaチームの皆様
