<template>
  <div id="app">
    <input type="text" v-model="inputValue" />
    <button v-on:click="addMemo">追加</button>
    <div>
      <div v-for="(tweet, index) in tweets" v-bind:key="index">
        {{ tweet.text }}
      </div>
    </div>
    <img v-bind:src="url" alt="画像" />
    <button v-on:click="getImage">更新</button>
  </div>
</template>

<script>
import firebase from "firebase"
export default {
  data: function() {
    return {
      url: "",
      tweets: [
        // {
        //   text: "はろー",
        // }
      ],
      inputValue: "",
    }
  },
  methods: {
    addMemo: function() {
      firebase
        .firestore()
        .collection("tweets")
        .add({
          text: this.inputValue,
          createdAt: firebase.firestore.FieldValue.serverTimestamp(),
        }) //ここまでで、コレクションに追加する処理
        .then((docRef) => {
          //あるdocを参照するもの
          docRef.get().then((docRef) => {
            this.tweets.push({
              id: docRef.id,
              text: docRef.data().text,
              createdAt: docRef.data().createdAt,
            })
          })
        })
    },
    getImage: function() {
      fetch("https://dog.ceo/api/breeds/image/random")
        .then((res) => {
          return res.json()
        })
        .then((json) => {
          this.url = json.message
        })
        .catch(() => {})
    },
  },
  created: function() {
    // ページが表示されたときにすぐ表示
    this.getImage()
    firebase
      .firestore()
      .collection("tweets")
      .orderBy("createdAt") //並べ替え
      // .where() //条件で絞り込む
      .get()
      .then((tweetsCollection) => {
        for (const doc of tweetsCollection.docs) {
          console.log(doc.id)
          console.log(doc.data())
          this.tweets.push({
            text: doc.data().text,
            createdAt: doc.data().createdAt,
          })
        }
      })
  },
}
</script>

<style></style>
