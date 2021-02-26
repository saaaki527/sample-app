<template>
  <div class="simple-memo" v-bind:style="{ backgroundColor: bgColor }">
    <slot />
    <!--<slot />でここに表示する内容を親コンポーネントが決められる -->
  </div>
</template>

<script>
export default {
  props: ["bgColor"],
}
</script>

<style scoped>
.simple-memo {
  margin: 4px;
  padding: 0.5rem;
  border-radius: 4px;
  background-color: orange;
  color: white;
}
</style>
