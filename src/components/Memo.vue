<template>
  <div>
    <input type="text" v-model="text" />
    <button v-on:click="addList">add</button>
    <div v-for="(T, i) in list" v-bind:key="i">{{ T }}</div>
  </div>
</template>

<script>
export default {
  name: "Memo", //これなくても動くのは動く。
  data: function() {
    return {
      text: "",
      list: [],
    }
  },
  methods: {
    addList: function() {
      this.list.push(this.text)
      this.text = ""
    },
  },
}
</script>

<style></style>
