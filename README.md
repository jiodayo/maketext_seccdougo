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

`.env` ファイルを開き、使用する API のキーを設定してください。

| 変数名 | 用途 | 取得先 |
|--------|------|--------|
| `OPENAI_API_KEY` | OpenAI 版（`app.py`）で使用 | [OpenAI Platform](https://platform.openai.com/api-keys) |
| `GOOGLE_API_KEY` | Google AI Studio 版（`app_google.py`）で使用 | [Google AI Studio](https://aistudio.google.com/app/apikey) |

```
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
GOOGLE_API_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

※ 使用するバージョンに対応するキーのみ設定すれば OK です。

## 起動

### OpenAI 版（gpt-4o）

```bash
streamlit run app.py
```

### Google AI Studio 版（Gemini）

```bash
streamlit run app_google.py
```

ブラウザが自動で開き、アプリが表示されます。

## 使い方

1. テキストエリアに講演のメモや書き起こしテキストを貼り付ける
2. 「🚀 レポートを生成」ボタンをクリック
3. 生成されたレポートが画面に表示される（コピー用プレーンテキストも展開可能）

## ファイル構成

| ファイル | 説明 |
|----------|------|
| `app.py` | OpenAI GPT（gpt-4o）版メインアプリ |
| `app_google.py` | Google AI Studio（Gemini）版メインアプリ |
| `requirements.txt` | 依存パッケージ一覧 |
| `.env.example` | 環境変数テンプレート |
| `.gitignore` | Git 除外設定 |

## 技術スタック

- **Python 3.10+**
- **Streamlit** — Web UI
- **OpenAI API** (gpt-4o) — テキスト生成（`app.py`）
- **Google Generative AI** (Gemini) — テキスト生成（`app_google.py`）
- **python-dotenv** — 環境変数管理
