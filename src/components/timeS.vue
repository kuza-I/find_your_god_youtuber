<template>
  <div class="timeslist">
    <div class="title">今週のスケジュール</div>
    <div>
      <div v-for="(subject, index) in timeS" v-bind:key="index" class="todo">
        <div class="todo__text todo__text--done">
          {{ subject.week }}日目 : {{ subject.time }}時間目 : {{ subject.text }}
        </div>
        <div class="todo__checkbox">
          <div>宿題</div>
          <input type="checkbox" v-model="subject.Homework" />
        </div>
        <div v-on:click="deleteTodo(index)" class="todo__delete">削除</div>
      </div>
    </div>
    <div>
      <div class="inputManager">
        <div>教科、日数、何時間目の順で入力</div>
        <input type="text" v-model="inputWork" />
        <input type="number" v-model="inputWeek" />
        <input type="number" v-model="inputTime" />

        <div v-on:click="addTimeS">追加</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputWork: "",
      inputWeek: 0,
      inputTime: 0,
      timeS: [
        {
          text: "国語",
          week: 1,
          time: 5,
          Homework: false,
        },
        {
          text: "数学",
          week: 5,
          time: 3,
          Homework: true,
        },
      ],
    }
  },
  methods: {
    addTimeS() {
      if (this.inputWork !== "") {
        const times = {
          text: this.inputWork,
          week: this.inputWeek,
          time: this.inputTime,
          Homework: false,
        }
        this.timeS.push(times)
      }
    },
    deleteTodo(index) {
      this.timeS.splice(index, 1)
    },
  },
}
</script>

<style>
.title {
  padding: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: lightpink;
}
.inputManager {
  margin: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.todo__text {
  display: flex;
  justify-content: center;
  align-items: center;
}

.todo__checkbox {
  display: flex;
  justify-content: center;
  align-items: center;
}
.todo__delete {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
