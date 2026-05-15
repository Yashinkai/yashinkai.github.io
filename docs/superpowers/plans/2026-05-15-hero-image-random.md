# ヒーロー画像ランダム表示 実装計画

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** トップページ（index.html）のヒーロー画像を、アクセスのたびに3種類からランダムで1枚表示する。

**Architecture:** `<img>` タグに id を付与し、既存の `<script>` 冒頭でランダムに src を書き換える。ローダーが非表示になる前に画像が確定するため、ちらつきなし。

**Tech Stack:** 素のHTML/JS（ビルドステップなし）

---

### Task 1: ヒーロー画像のランダム表示実装

**Files:**
- Modify: `index.html:198`（img に id 付与）
- Modify: `index.html:342`（script 冒頭にランダム選択コード追加）

- [ ] **Step 1: `<img>` に `id="heroImg"` を付与する**

`index.html` 198行目を以下に変更：

```html
<img id="heroImg" src="トップページ.png" alt="野心会" style="width:100vw;height:calc(100vh - 64px);display:block;object-fit:cover;object-position:center top;margin-left:calc(50% - 50vw);margin-top:64px;" />
```

- [ ] **Step 2: script 冒頭にランダム選択コードを追加する**

`index.html` の `<script>` ブロック（340行目）の直後、`// Loader` のIIFEより前に以下を追加：

```js
(function () {
  const heroImages = ['トップ（赤）.png', 'トップ（青）.png', 'トップ（黄）.png'];
  document.getElementById('heroImg').src = heroImages[Math.floor(Math.random() * heroImages.length)];
})();
```

- [ ] **Step 3: ブラウザで動作確認する**

`index.html` をブラウザで開き、リロードするたびにヒーロー画像が3種類の中からランダムで変わることを確認する。

- [ ] **Step 4: コミットする**

```bash
git add index.html
git commit -m "ヒーロー画像をアクセスのたびにランダム表示（3種類）"
```
