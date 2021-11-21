<template>
  <div class="YTRank">
    <div>
      <input type="text" v-model="inputKey" />
      <div v-on:click="addWords">追加</div>
    </div>
    <div class="searchtext">
      <div
        v-for="(KeyWord, index) in KeyWords"
        v-bind:key="index"
        class="KeyWords"
      >
        <div class="KeyWord__text">{{ index }}:{{ KeyWord.text }}</div>
        <div v-on:click="SearchWord(KeyWord.text)" class="Word__search">
          検索
        </div>
        <div v-on:click="deleteWord(index)" class="Word__delete">削除</div>
      </div>
    </div>
    <div class="findMove">you chose:{{ params.q }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputKey: "",
      KeyWords: [],
      info: null,
      params: {
        type: "video",
        part: "snippet",
        q: "world",
        order: "date",
        pageToken: "",
        key: "{AIzaSyA7Y3MPyMFnBv7txO8ansQ7kZy0op09DLA}",
      },
    }
  },
  methods: {
    addWords() {
      if (this.inputKey !== "") {
        const thiswords = { text: this.inputKey }
        this.KeyWords.push(thiswords)
      }
    },
    deleteWord(index) {
      this.KeyWords.splice(index, 1)
    },
    SearchWord(text) {
      this.params.q = text
    },
  },
}
</script>

<style>
.YTRank {
  padding: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: lightblue;
}

.searchtext {
  margin: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.KeyWord__text {
  margin: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
.Word__search {
  display: flex;
  justify-content: center;
  align-items: center;
}
.Word__delete {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
