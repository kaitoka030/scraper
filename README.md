## Webスクレイピング テンプレート（Python）

このリポジトリは、**Pythonを使ったWebスクレイピングの基本テンプレート**です。  
`requests` と `BeautifulSoup` を用いて、HTMLデータの取得・解析を行う最小構成をまとめています。  

---

### 機能概要
- HTTPリクエストを送信してWebページを取得  
- タイムアウト・エラー処理を実装  
- Bot検知回避のためのUser-Agent指定  
- BeautifulSoupを使ったHTML解析準備  
- 処理の間隔を調整（`time.sleep()`）

---

### 使用方法

```bash
# 必要なライブラリをインストール
pip install requests beautifulsoup4
```

```python
import requests
from bs4 import BeautifulSoup
import time

url = "https://example.com"

headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
}

try:
    r = requests.get(url, headers=headers, timeout=10)
    r.encoding = r.apparent_encoding
    r.raise_for_status()
    soup = BeautifulSoup(r.text, "html.parser")
except Exception as e:
    print(f"エラーが発生しました：{e}")

time.sleep(1)

# 以下に要素を解析する処理を記述
```

---

### 注意事項

- 本コードは**学習・検証目的専用**です。  
- 対象サイトの**利用規約やrobots.txt**を必ず確認してください。  
- サイトに過度なリクエストを送信するとアクセス制限の対象になる場合があります。  
- 商用利用・自動購入・不正アクセス等は禁止されています。  

---

### 補足情報

| ライブラリ | 用途 |
|-------------|------|
| `requests` | Webページの取得 |
| `BeautifulSoup` | HTML解析 |
| `time` | 処理間隔の調整 |

---

### 関連リソース
- [BeautifulSoup 公式ドキュメント](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Requests 公式ドキュメント](https://requests.readthedocs.io/en/latest/)

---

### 作者より
このテンプレートは、PythonによるWebスクレイピング学習をスムーズに始めるための基本構成です。  
これをベースに、取得データの整形・保存・自動化などに発展させていくことができます。
