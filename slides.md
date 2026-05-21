---
layout: center
highlighter: shiki
css: unocss
colorSchema: dark
transition: fade-out
title: Slidev テンプレート
lineNumbers: false
drawings:
  persist: false
mdc: true
clicks: 0
preload: false
glowSeed: 229
routerMode: hash
---

<div translate-x--14>

<h1>
  Slidev テンプレート
</h1>

日本語ベースのシンプルなプレゼンテーション

</div>

---
layout: intro
class: px-24
glowSeed: 205
---

# プレゼンテーションへようこそ

このテンプレートを使用してスライドを作成できます。

---

# スライドの基本構成

スライドは `---` で区切られます。各スライドの先頭に YAML フロントマターを追加：

```yaml
---
layout: center      # レイアウトの指定
class: px-24        # カスタムクラス
glowSeed: 205       # 背景グロー効果
---
```

---

# レイアウトの種類

- **center**: コンテンツを中央に配置
- **intro**: タイトルスライド用
- **cover**: カバースライド
- **statement**: テキストフォーカス
- **two-cols**: 2カラムレイアウト

---
layout: two-cols
---

# 左側のコンテンツ

- ポイント1
- ポイント2
- ポイント3

::right::

# 右側のコンテンツ

こちらに別のコンテンツを配置できます。

---

# UnoCSS スタイリング

<div grid grid-cols-2 gap-4 mt-6>
<div border="2 solid white/5" rounded-lg bg="white/5" p-4>
  <div font-semibold text-lg mb-2>カード1</div>
  <div text-sm opacity-70>サンプルコンテンツ</div>
</div>

<div border="2 solid white/5" rounded-lg bg="white/5" p-4>
  <div font-semibold text-lg mb-2>カード2</div>
  <div text-sm opacity-70>サンプルコンテンツ</div>
</div>
</div>

---

# インタラクティブな要素

<div v-click flex flex-col gap-4 mt-6>
  <div border-l-4 border-blue-400 pl-4 py-2>
    <div font-semibold>クリックで表示</div>
    <div text-sm opacity-70 mt-1>このコンテンツはクリックで表示されます</div>
  </div>
</div>

<div v-click flex flex-col gap-4 mt-4>
  <div border-l-4 border-green-400 pl-4 py-2>
    <div font-semibold>次のクリックで表示</div>
    <div text-sm opacity-70 mt-1>段階的なアニメーションが可能です</div>
  </div>
</div>

---

# コード例

スライド内にコードを埋め込めます。

```typescript
// 例: TypeScript コード
const greeting = (name: string) => {
  return `Hello, ${name}!`;
};

console.log(greeting("Slidev"));
```

---

# リスト表示

<div v-clicks grid grid-cols-2 gap-6 mt-6>
<div>
  <div font-semibold mb-3 text-blue-300>項目1</div>
  <ul text-sm space-y-2 opacity-80>
    <li>• 詳細A</li>
    <li>• 詳細B</li>
    <li>• 詳細C</li>
  </ul>
</div>

<div>
  <div font-semibold mb-3 text-green-300>項目2</div>
  <ul text-sm space-y-2 opacity-80>
    <li>• 特徴1</li>
    <li>• 特徴2</li>
    <li>• 特徴3</li>
  </ul>
</div>
</div>

---

# よく使うスタイルクラス

| クラス | 説明 |
|--------|------|
| `flex`, `grid` | レイアウト |
| `gap-4` | 要素間の余白 |
| `rounded-lg` | 角丸 |
| `bg="white/5"` | 半透明背景 |
| `text-sm`, `text-lg` | フォントサイズ |
| `font-semibold` | 太字 |
| `opacity-70` | 透明度 |

---
layout: center
class: text-center
---

# ご視聴ありがとうございました

詳細は README.md を参照してください
