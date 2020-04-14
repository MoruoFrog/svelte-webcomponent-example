# Svelte 编译成web component

## build
```bash
npm run build
```

## 原生html当中使用
```bash
cd public
http-server .
```

## Vue 当中使用
```
cd vue-example
npm i
npm run serve
```

## 注意

Svelte 通过dispatch emit的自定义事件，编译成webcomponent之后不能直接通过addEventListener监听，需要通过$on方法去监听。所以也不能在Vue的模版中通过v-on监听。需要手动dispatch一个new CustomEvent

## 链接
[Custom Elements Everywhere](https://custom-elements-everywhere.com/)