# レスポンシブSassライブラリ

レスポンシブ用のメディアクエリの記述を、Sassのmixin集としてまとめたもの。  

## ブレイクポイント

- xs〜sm
  スマホサイズ
- sm〜md
  タブレットサイズ
- md〜lg
  ノートPCサイズ
- lg〜xl
  デスクトップPCサイズ

```scss
$breakpoints : (
  "xs": ("min": "1px", "max": "399px"),
  "sm": ("min": "400px", "max": "799px"),
  "md": ("min": "800px", "max": "999px"),
  "lg": ("min": "1000px", "max": "1199px"),
  "xl": ("min": "1200px")
) !default;
```

## レスポンシブの例

任意のファイルで、mixinの定義ファイルを呼び出す。

```scss
@use './_responsiveMediaQuery.scss' as mq;
```

### スマホでのみ縦並び、その他は横並びのレイアウト

```scss
.nav-bar {
    // デフォルトは縦並び
    display: flex;
    justify-content: center;
    flex-direction: column;

    // md以上で横並びに切り替え
    @include mq.md {
        flex-direction: row;
    }
}
```

### 特定のサイズでのみスタイルを適用

```scss
.toggleIcon {
    display: none;
    
    // mdでのみ要素を表示
    @include mq.only(xs) {
        display: block;
    }
}
```

### 特定のサイズでのみ要素を表示

```scss
.toggleIcon {
    // xsでのみ表示
    @include mq.only-show(xs);
}
```

### 一定範囲のサイズでのみスタイルを適用

```scss
.appStoreLink {
    display: none;
    
    // スマホとタブレットでのみ表示
    @include mq.range(xs, sm) {
        display: block;
    }
}
```

### 一定範囲のサイズでのみ要素を表示

```scss
.appStoreLink {

    // スマホとタブレットでのみ表示
    @include mq.range-show(xs, sm);
}
```
