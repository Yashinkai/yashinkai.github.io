# トップページヒーロー画像ランダム表示 設計書

## 概要

トップページ（`index.html`）のヒーロー画像を、アクセスのたびにランダムで3種類から1枚表示する。

## 対象ファイル

- `index.html`

## 使用画像

- `トップ（赤）.png`
- `トップ（青）.png`
- `トップ（黄）.png`

## 変更内容

### 1. `<img>` に id を付与（198行目）

```html
<img id="heroImg" src="トップページ.png" ...>
```

### 2. 既存 `<script>` ブロックにランダム選択コードを追加

```js
const heroImages = ['トップ（赤）.png', 'トップ（青）.png', 'トップ（黄）.png'];
document.getElementById('heroImg').src = heroImages[Math.floor(Math.random() * heroImages.length)];
```

ページロード時に即時実行。ローダーが非表示になる前に画像 src が確定するため、表示のちらつきが起きない。

## 非変更事項

- ローダーアニメーション
- フェードイン処理
- その他のページ・ファイル
