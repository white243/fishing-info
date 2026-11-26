# fishing-info

釣り情報をまとめる静的サイトです。
`pages/` フォルダにファイルを置くと、自動で Web に公開されます。

**公開URL:** https://white243.github.io/fishing-info/

---

## しくみ

```
pages/ にファイルを追加・更新する（main ブランチ）
        ↓ 自動
GitHub Actions が pages/ の中身をデプロイする
        ↓ 数分ほどで
公開URLに反映される
```

- 公開されるのは **`pages/` の中身だけ** です（`README.md` などは公開されません）
- `pages/index.html` がトップページ（`https://white243.github.io/fishing-info/`）になります
- `pages/spots.html` を置けば `https://white243.github.io/fishing-info/spots.html` で見られます

> ⚠️ `pages/` に置いたものは **誰でも見られる状態** になります。
> 個人情報やパスワードなどは絶対に置かないでください。

---

## はじめに（最初の1回だけ）

1. リポジトリへの招待メールが届くので、**「Accept invitation」** を押して参加する
2. GitHub にログインした状態で、このリポジトリを開けることを確認する

---

## ファイルをアップロードする方法

### 方法1：パソコンのブラウザから（おすすめ）

1. 次のページを開く
   👉 https://github.com/white243/fishing-info/tree/main/pages
   （画面上部のパスが `fishing-info / pages /` になっていればOK）
2. 右上の **「Add file」** → **「Upload files」** を押す
3. アップロードしたいファイル（またはフォルダ）を画面にドラッグ＆ドロップする
   - フォルダごとドロップすると、フォルダ構成のままアップロードできます
4. 下の **「Commit changes」** 欄に、何をしたか簡単に書く（例：`釣り場の写真を追加`）
5. **「Commit directly to the main branch」** が選ばれていることを確認して、**「Commit changes」** を押す
6. 数分待ってから公開URLを開き、反映されているか確認する

> 💡 必ず **`pages/` フォルダを開いた状態で** アップロードしてください。
> リポジトリのトップでアップロードすると `pages/` の外に置かれてしまい、公開されません。

### 方法2：スマホから

- **ファイル（画像など）のアップロード**は、スマホの **ブラウザ** で方法1と同じページを開いて、同じ手順で行えます
  （「Add file」が見当たらない場合は、ブラウザのメニューから「PCサイトを表示」に切り替えてください）
- **GitHub アプリ** でも、すでにある HTML などのテキストファイルを開いて、その場で編集・コミットできます。ちょっとした文字の修正に便利です

### 方法3：git を使う（わかる人向け）

git コマンドに慣れている場合は、clone して push してもOKです。

```bash
git clone https://github.com/white243/fishing-info.git
cd fishing-info
# pages/ 配下にファイルを追加・編集
git add pages/
git commit -m "釣り場ページを追加"
git push origin main
```

---

## 既存ファイルの更新・削除

- **上書き**：同じ名前のファイルをもう一度アップロードすると、上書きされます
- **編集**：ファイルを開いて右上の ✏️（鉛筆アイコン）から、ブラウザ上で直接編集できます
- **削除**：ファイルを開いて右上の「…」メニュー → **「Delete file」**

どの操作も、最後に **「Commit changes」** を押すと確定し、公開サイトにも反映されます。

---

## ファイルを作るときの注意

### フォルダ構成の例

```
pages/
├── index.html        ← トップページ（必須）
├── css/
│   └── style.css
├── js/
│   └── main.js
└── images/
    └── fish.png
```

### パスは「相対パス」で書く

公開URLが `/fishing-info/` の下になるため、**先頭に `/` を付けると読み込めません**。

```html
<!-- ✅ OK -->
<link rel="stylesheet" href="css/style.css">
<script src="js/main.js"></script>
<img src="images/fish.png" alt="魚">

<!-- ❌ NG（先頭の / があると表示されない） -->
<link rel="stylesheet" href="/css/style.css">
```

- サブフォルダの HTML から参照するときは `../images/fish.png` のように1つ上の階層を指定します
- CSS の中の `url()` は、**CSSファイルの場所が基準** です（例：`css/style.css` からは `url(../images/bg.png)`）

### その他

- **ファイル名の大文字・小文字は区別されます**（`Fish.png` と `fish.png` は別物）。ファイル名は半角英数字の小文字で統一するのがおすすめです
- ブラウザからアップロードできるのは **1ファイル25MBまで** です
- 反映されないときは、数分待つ・ブラウザを再読み込み（スーパーリロード）する・リポジトリの **「Actions」** タブで処理が ✅ になっているか確認する、の順で試してください
