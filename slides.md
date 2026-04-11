---
# try also 'default' to start simple
theme: default
title: 【令和最新版】AviUtl2のプラグインを作ろう！
info: |
  電通大技術系サークル合同新歓2026の発表資料です。
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
fonts:
  sans: "M PLUS 1p"
  weights: 400,700
---

<div class="font-[Microsoft_YaHei]">

# 【令和最新版】AviUtl2のプラグインを作ろう！

</div>

名無し。（@sevenc_nanashi / sevenc7c.com）

---

# AviUtl2、使ってますか？

- 正式名称：AviUtl ExEdit2
- AviUtlの正統後継ソフトウェア
- 2025/7/7に2.00 beta1がリリース
- 毎週土曜日または日曜日に更新
- 現在は2.00 beta40a

---

# 変更点

- 64bit化
- UTF-8対応
- プラグインAPIの刷新・拡張
- パッケージフォーマットの確立（.au2pkg.zip）

## コミュニティ側の変化

- 巨大コミュニティの誕生（「AviUtl2の情報が知りたいだろって！！」）
- 主流と呼べるパッケージマネージャーの誕生（AviUtl2 カタログ）
- GitHubでのプラグイン・スクリプト配布の増加

---
transition: fade

---

# AviUtl1のプラグインの作り方

- AviUtl SDK（zip）をダウンロード
  - 必要に応じてShift-JISからUTF-8に変換
- C++でコードを書く
- Visual StudioやCMakeでDLLをビルド
- AviUtl1のフォルダにDLLをコピー
- AviUtl1を起動して動作確認

---

# AviUtl2のプラグインの作り方

- AviUtl2 SDK（zip）をダウンロード
  - 必要に応じてShift-JISからUTF-8に変換
- C++でコードを書く
- Visual StudioやCMakeでDLLをビルド
- AviUtl2のpluginフォルダにDLLをコピー
- AviUtl2を起動して動作確認
- （au2pkg.zipでパッケージ化して配布）

---
transition: fade

---

<div  un-text-center un-h-full un-grid un-items-center>

## zipダウンロード+再エンコード... <twemoji-tired-face />

</div>

---

<div un-text-center un-h-full un-grid un-items-center>

## aviutl2_sdk_mirror！<twemoji-smiling-face-with-smiling-eyes />

</div>

---

# aviutl2_sdk_mirror

- https://github.com/aviutl2/aviutl2_sdk_mirror
- AviUtl2 SDKのGitHubミラー
- 文字コードがUTF-8（元はShift-JIS）
- `include`や`examples`への整理
- 説明文がMarkdownに
- 2026/8/17にInitial commit

<v-click>

- 管理者は私です <img un-h="30" src="./i-made.jpg" un-inline />

</v-click>

---
transition: fade

---

# AviUtl2のプラグインの作り方

- AviUtl2 SDK（zip）をダウンロード
  - 必要に応じてShift-JISからUTF-8に変換
- C++でコードを書く
- Visual StudioやCMakeでDLLをビルド
- AviUtl2のpluginフォルダにDLLをコピー
- AviUtl2を起動して動作確認
- （au2pkg.zipでパッケージ化して配布）

---

# AviUtl2のプラグインの作り方\_改善版

- **aviutl2_sdk_mirrorをsubmoduleとしてクローン**

<div un-relative un-h="[1.8em]" />

- C++でコードを書く
- Visual StudioやCMakeでDLLをビルド
- AviUtl2のpluginフォルダにDLLをコピー
- AviUtl2を起動して動作確認
- （au2pkg.zipでパッケージ化して配布）

---
transition: fade

---

<div  un-text-center un-h-full un-grid un-items-center>

## ビルド+コピー+パッケージ化用のスクリプト：面倒 <twemoji-tired-face />

</div>

---

<div un-text-center un-h-full un-grid un-items-center>

## aviutl2-cli！<twemoji-smiling-face-with-smiling-eyes />

</div>

---

# aviutl2-cli

- https://github.com/sevenc-nanashi/aviutl2-cli
- AviUtl2のプラグイン・スクリプトの開発環境を構築するツール
- ビルドコマンドとビルド元と配置先を書けば1コマンドでテスト環境ができる
  - `au2 prepare` でテスト用環境の構築
  - `au2 dev` でビルド+コピー+動作確認
- パッケージも1コマンドで作れる（`au2 release`）

<v-click>

- 開発者は私です <img un-h="35" src="./i-made.jpg" un-inline />

</v-click>

---
transition: fade

---

# AviUtl2のプラグインの作り方\_改善版

- aviutl2_sdk_mirrorをsubmoduleとしてクローン
- C++でコードを書く
- Visual StudioやCMakeでDLLをビルド
- AviUtl2のpluginフォルダにDLLをコピー
- AviUtl2を起動して動作確認
- （au2pkg.zipでパッケージ化して配布）

---

# AviUtl2のプラグインの作り方\_改善版(2)

- aviutl2_sdk_mirrorをsubmoduleとしてクローン
- C++でコードを書く
- **Visual StudioやCMakeでDLLのビルド環境を構築**
- **`au2 prepare` -> `au2 dev` でビルド+コピー+動作確認**
- **独立したAviUtl2環境で動作確認**
- **`au2 release` でパッケージ化して配布**

---

<div  un-h-full un-grid un-items-center un-text-center>

## C++... <twemoji-persevering-face /><twemoji-tired-face /><twemoji-weary-face />

</div>

---

# C++の問題点

<v-clicks>

- パッケージが分散している
- 依存関係の管理が面倒
- 型推論が比較的弱い
- 勝手にコピーが走って事故りやすい（n敗）
- 古い仕様に引きずられている
- キャラクターがかわいくない
- <span un-font="bold [Microsoft_YaHei]">令和最新版</span>ではない

</v-clicks>

---

<div un-grid un-items-center un-h-full un-text="[#f85207]" un-text-center>

## Rewrite It In Rust！

</div>

---

<h1 un-text="[#f85207]">
Rustのうれしいところ
</h1>

<v-clicks>

- 中央集権のパッケージマネージャー（crates.io）
- 型推論が強力
- 重量コピーが明示的
- 互換性を保ったまま仕様を進化させやすい（Edition）
- どのエディタでも快適に書ける
- キャラクターがかわいい
- <span un-font="bold [Microsoft_YaHei]">令和最新版</span>

</v-clicks>

<img v-click="6" src="./ferrs.png" un-h="[50%]" un-absolute un-right="0" un-top="40" un-pointer-events-none />

---
transition: fade

---

<div un-grid un-items-center un-h-full un-text-center>

## でも公式SDKってC++でしょ？

</div>

---

<div un-grid un-items-center un-h-full un-text-center un-text="[#f85207]">

## Rust版SDK、あります

</div>

---

# <span un-text="[#f85207]">aviutl2-rs</span>

- AviUtl2のプラグインをRustで書くためのライブラリ
- 採用実績：AviUtl2カタログのパッケージのおおよそ1/6はaviutl2-rs製[^1][]
- 2026/7/13にv0.1.0をリリース
- 現在v0.22.0
- 採用実績：Rusty Scripts Search Plugin、ntsc-rs.anm2、clipboard.aux2など

<v-click>

- 開発者は私です <img un-h="30" src="./i-made.jpg" un-inline />

</v-click>

[^1]: 181パッケージ中32パッケージ（2026/4/11現在）

---
transition: fade

---
# AviUtl2のプラグインの作り方\_改善版(2)

- aviutl2_sdk_mirrorをsubmoduleとしてクローン
- C++でコードを書く
- Visual StudioやCMakeでDLLのビルド環境を構築
- `au2 prepare` -> `au2 dev` でビルド+コピー+動作確認
- 独立したAviUtl2環境で動作確認
- `au2 release` でパッケージ化して配布

---

# <span un-font="bold [Microsoft_YaHei]" un-text="[#f85207]">【令和最新版】AviUtl2プラグインの作り方</span>

- **`cargo add aviutl2` でSDKをプロジェクトに追加**
- **Neovimなどの好きなエディタでRustでプラグインを書く**
- `au2 prepare` -> `au2 dev` でビルド+コピー+動作確認
- 独立したAviUtl2環境で動作確認
- `au2 release` でパッケージ化して配布
---

# まとめ

- aviutl2_sdk_mirrorでSDKの入手と管理を楽に
- aviutl2-cliでテスト環境の構築とパッケージ化を楽に
- aviutl2-rsでRustでプラグインが書ける

<div un-h="4" />

- 令和最新版のAviUtl2プラグイン開発環境で快適な開発をしよう！

<v-click>

<div un-h="20" />

### おまけ

- Rust製プラグイン32個のうち、私が開発したのは30個です

</v-click>
