<template>
  <div class="app">
    <simple-memo>メモ１</simple-memo>
    <simple-memo>メモ２</simple-memo>
    <simple-memo v-for="memo in memos" v-bind:key="memo.id">
      {{ memo.text }}
    </simple-memo>
  </div>
</template>

<script>
import SimpleMemo from "./components/SimpleMemo.vue"

export default {
  components: { SimpleMemo },
  data() {
    return {
      memos: [
        { id: 0, text: "メモ１" },
        { id: 1, text: "メモ２" },
      ],
    }
  },
}
</script>

<style></style>
