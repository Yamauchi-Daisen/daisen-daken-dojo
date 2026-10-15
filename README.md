# ダイセン打鍵道場（DDD）

社内向けのタッチタイピング練習ゲームです。瓦割り（訓練）、連撃（耐久）、格闘（実戦）の3モードと、段位・成長記録・四天王（上位4名）があります。

## 構成

| ファイル | 役割 |
|---|---|
| `app.py` | Streamlit の入口。ゲームを画面いっぱいに表示するだけ |
| `game/index.html` | ゲーム本体（1ファイルで完結） |
| `gas/Code.gs` | 記録を受け付ける Google Apps Script（スプレッドシート「Ash打鍵道場 記録」に設定済み） |
| `requirements.txt` | Streamlit のバージョン指定 |
| `.streamlit/config.toml` | 画面の色やメニュー表示の設定 |

## 手元で動かす

```
pip install -r requirements.txt
streamlit run app.py
```

## 記録の仕組み

- 稽古の結果は、ゲームから Google Apps Script のWebアプリへ送られ、スプレッドシートに書き込まれます
- 送り先のアドレスは `game/index.html` の `RANK_URL` に書かれています
- `gas/Code.gs` を変えたときは、Apps Script で「デプロイを管理」→ 編集 → 新バージョン でデプロイします（アドレスは変わりません）
- 個人の成長記録・設定・苦手キーは、遊んだ人のブラウザに保存されます

## ゲームを更新するとき

`game/index.html` を差し替えて GitHub に push すると、Streamlit Community Cloud が自動で更新します。

---
Studio Ash Products
