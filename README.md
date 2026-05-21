# スライドテンプレート

Slidev テンプレートベースのプレゼンテーション。モダンなUIデザイン、インタラクティブなアニメーション、ダークテーマを備えています。

> **Note**: このテンプレートは [BaizeAI/talks](https://github.com/BaizeAI/talks/tree/main/packages/2025-06-11-kubecon-hk) をベースにしています。

## クイックスタート

```bash
pnpm install
pnpm dev
```

ブラウザで http://localhost:3030 を開くと、自動的にスライドが表示されます。

## GitHub Pages 公開設定

このテンプレートは GitHub Actions で自動的に GitHub Pages へ公開できるワークフローを備えています。

### セットアップ手順

1. **リポジトリ設定を確認**
   - GitHub リポジトリの Settings → Pages にアクセス
   - Source: "Deploy from a branch" を選択
   - Branch: `gh-pages` / `(root)` を選択して Save

2. **公開を有効化**
   - `publish.config.yml` の `enabled` を `true` に変更
   ```yaml
   github_pages:
     enabled: true   # 変更
   ```

3. **push して自動公開**
   ```bash
   git add publish.config.yml
   git commit -m "Enable GitHub Pages publishing"
   git push
   ```

4. **公開 URL**
   - `https://<your-username>.github.io/<repo-name>/`

### 手動公開（テスト時）

`publish.config.yml` の設定に関わらず強制的に公開する場合：
- GitHub リポジトリの **Actions** タブから `Publish to GitHub Pages` ワークフローを選択
- **Run workflow** → `force_publish: true` にチェックして実行

## スタイルガイド

このテンプレートは以下の技術を使用しています：

### 1. スライドのレイアウト

スライドの冒頭に YAML フロントマターでレイアウトと設定を指定します：

```yaml
---
layout: center          # center, intro, cover, statement, image-right など
class: px-24            # 追加のカスタムクラス
glowSeed: 205           # 背景グロー効果のシード値（1-360）
---
```

**主なレイアウト：**
- `center`: コンテンツを中央に配置
- `intro`: タイトルスライド用
- `cover`: カバースライド
- `statement`: テキストフォーカス
- `two-cols`: 2カラムレイアウト

### 2. UnoCSS / Tailwind スタイリング

属性モードで直接 HTML 要素にクラスを指定：

```html
<!-- サイズ指定 -->
<div w-50 h-50>Content</div>  <!-- width: 200px, height: 200px -->

<!-- パディング・マージン -->
<div px-4 py-3>Content</div>  <!-- padding-x: 1rem, padding-y: 0.75rem -->

<!-- フレックスボックス -->
<div flex items-center justify-center gap-4>Items</div>

<!-- テキストスタイル -->
<span font-semibold text-3xl>Large Bold Text</span>

<!-- 背景・枠線 -->
<div bg="white/5" border="2 solid white/5" rounded-lg>Card</div>

<!-- 背景ぼかし -->
<div backdrop-blur-sm bg="white/10">Blur effect</div>
```

**よく使うクラス：**
- `flex`, `grid`: レイアウト
- `items-center`, `justify-center`: 配置
- `gap-x`: 要素間の余白
- `text-sm`, `text-xl`: フォントサイズ
- `font-semibold`, `font-medium`: 太さ
- `rounded-lg`: 角丸
- `opacity-70`: 透明度
- `translate-x-`, `translate-y-`: 移動
- `scale-`, `rotate-`: スケール・回転

### 3. インタラクティブな要素

Vue ディレクティブを使用してアニメーションやクリック制御を実装：

```html
<!-- クリックで表示/非表示 -->
<div v-click flex flex-col gap-2
  :class="$clicks < 1 ? 'opacity-0' : 'opacity-100'"
>
  Content appears on click
</div>

<!-- 複数回クリックでの制御 -->
<div v-click="2" ...>Content appears on 3rd click</div>

<!-- 前のクリック後に表示 -->
<div v-after ...>Content after previous click</div>

<!-- アニメーション設定 -->
<div transition duration-500 ease-in-out>Smooth animation</div>
```

**ディレクティブ：**
- `v-click`: クリックトリガー
- `v-click="n"`: n回目のクリック後
- `v-after`: 前の要素クリック後

### 4. アイコン

Iconify を使用したアイコンシステム：

```html
<!-- Carbon アイコン -->
<div i-carbon:warning-alt text-amber-300 />

<!-- Devicon -->
<div i-devicon:kubernetes text-6xl />

<!-- Remix Icons -->
<div i-ri:github-fill />
```

**アイコンセット：**
- `i-carbon:*`: IBM Carbon Design
- `i-devicon:*`: DevIcon
- `i-ri:*`: Remix Icons

### 5. 画像の配置

画像は `public/` ディレクトリに配置し、相対パスで参照：

```html
<img src="./public/KubeCon.svg" h-20 />
<img src="./public/person/peter.png" w-50 h-50 rounded-full />
```

### 6. レスポンシブグリッド

複数カラムレイアウト：

```html
<div grid grid-cols-3 gap-3 h-75>
  <div border="2 solid white/5" rounded-lg bg="white/5">Card 1</div>
  <div border="2 solid white/5" rounded-lg bg="white/5">Card 2</div>
  <div border="2 solid white/5" rounded-lg bg="white/5">Card 3</div>
</div>
```

## テンプレートとして使用する場合

### ステップ1: 新しいスライド作成

```markdown
---
layout: center
class: px-24
glowSeed: 150
---

# Your Title Here

Your content
```

### ステップ2: ダークテーマのカード

```html
<div border="2 solid white/5" rounded-lg overflow-hidden bg="white/5" backdrop-blur-sm h-full>
  <div flex items-center bg="white/10" backdrop-blur px-3 py-2 rounded-md>
    <div i-carbon:icon-name text-color-300 text-sm mr-2 />
    <div font-semibold>Card Title</div>
  </div>
  <div px-4 py-3>
    <!-- Content -->
  </div>
</div>
```

### ステップ3: プロフィールセクション

```html
<div flex flex-col items-center>
  <img src="./public/person/image.png" w-50 h-50 rounded-full object-cover mb-5>
  <span font-semibold text-3xl>Name</span>
  <div text-sm opacity-70>Title</div>
</div>
```

### ステップ4: エクスポート

```bash
pnpm export    # PDF + 画像をエクスポート
pnpm build     # 本番向けビルド
```

## カラーパレット

ダークテーマ対応：
- テキスト: `white`, `white/70` (グレー)
- 背景: `white/5`, `white/10` (半透明白)
- アクセント: `amber-300`, `blue-300`, `green-300`
- テーマカラー: `#5791f7` (Kubernetes Blue)

## 参考リンク

- [Slidev Documentation](https://sli.dev/)
- [UnoCSS](https://uno.css/)
- [Iconify Icons](https://iconify.design/)
- [Template Reference](https://docs.google.com/presentation/d/17iv41llVvtgw7JssTzfHkLAncU9eGb2v/edit?slide=id.p1#slide=id.p1)

> Template originally created for KubeCon CloudNativeCon China 2025
