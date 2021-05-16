# gogoro

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## Issue

1.  編譯時一直出現 unexpected token "indent" 問題

```
解： pug的縮排都是有意義的，因此第一行不允許縮排
```

2. pug 要將 props 傳給子組件，無法正常顯示

```
解：不能使用縮寫的:props方式傳，需寫完整的v-bind:props
```

3. 編譯出現警告 [Vue warn]: Failed to resolve component: string at <Home onVnodeUnmounted=fn<onVnodeUnmounted> ref=Ref

```
解：pug單行敘述中，無法辨識出<string></string>這個tag，移除即可
```
