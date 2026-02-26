# 講演レポート生成アプリ

講演のメモや書き起こしテキストを入力すると、OpenAI GPT（gpt-4o）かGemini AIを使って約 350〜400 文字の構造化されたイベントレポートを自動生成する Streamlit Web アプリです。

## 生成されるレポートの構成

| 段落 | 内容 |
|------|------|
| タイトル | セクション名（短い見出し） |
| 導入 | 登壇者の紹介、対談テーマ、趣旨説明 |
| 本論 | 講演内容の要約 |
| 結論・補足 | 付加的な議論（目利き、キャリア等） |

## セットアップ

### 1. リポジトリをクローン / ディレクトリに移動

```bash
cd maketext_seccdougo
```

### 2. Python 仮想環境の作成（推奨）

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. パッケージのインストール

```bash
pip install -r requirements.txt
```

### 4. 環境変数の設定

```bash
cp .env.example .env
```

`.env` ファイルを開き、`OPENAI_API_KEY` に実際の API キーを設定してください。

```
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

API キーは [OpenAI Platform](https://platform.openai.com/api-keys) から取得できます。

## 起動

```bash
streamlit run app.py
```

ブラウザが自動で開き、アプリが表示されます。

## 使い方

1. テキストエリアに講演のメモや書き起こしテキストを貼り付ける
2. 「🚀 レポートを生成」ボタンをクリック
3. 生成されたレポートが画面に表示される（コピー用プレーンテキストも展開可能）

## 技術スタック

- **Python 3.10+**
- **Streamlit** — Web UI
- **OpenAI API** (gpt-4o) — テキスト生成
- **python-dotenv** — 環境変数管理
