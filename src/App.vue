<template>
  <div id="app" class="container">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <Memo />
    <Human />
    <!-- 3. 普通の HTML のタグのように Human コンポーネントを書く -->
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue"
import Memo from "./components/Memo.vue"
import Human from "@/components/Human.vue" // 1. Human コンポーネントを Human.vue から読み込む
// @はsrcディレクトリを指す。@/～は絶対パス、./は相対パス

export default {
  name: "App",
  components: {
    HelloWorld,
    Memo,
    Human, // 2. Human コンポーネントを App.vue の中で使えるように登録する
    // 省略記法が使われている
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: red;
  margin-top: 60px;
}
</style>
