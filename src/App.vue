<template>
  <div id="app">
    <div class="hello-wrold">
      <div class="hello-wrold__message">
        {{ message }}
      </div>
    </div>

    <YTRanking />

    <timeS />
  </div>
</template>

<script>
import YTRanking from "@/components/YTRank.vue"
import timeS from "@/components/timeS.vue"
export default {
  name: "App",
  components: {
    YTRanking,
    timeS,
  },
  data: function () {
    return {
      message: "あなたの好きなジャンルはなんですか？",
    }
  },
  methods: {},
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>

<style scoped>
.hello-wrold {
  margin: 60px;
  text-align: center;
}

.hello-wrold .hello-world__message {
  font-size: 50px;
  color: #2c3e50;
}
</style>
