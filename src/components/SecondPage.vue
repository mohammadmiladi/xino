<template>
  <div class="main-second">
    <div class="main-container">
      <div class="question">{{ questionsData[currentQuestion].question }}</div>
      <div class="timer">
          
      </div>
      <div
        v-for="(answers, idx) in shuffle(
          questionsData[currentQuestion].answers
        )"
        :key="idx"
        class="answers"
      >
        {{ answers }}
      </div>
      <div class="show-answer"></div>
    </div>
  </div>
</template>

<script>
import Questions from "../../questions/questions.json";

export default {
  name: "secondPage",
  data() {
    return {
      questionsData: [],
      currentQuestion: 0,
    };
  },
  created() {
    this.questionsData = Questions;
  },
  methods: {
    shuffle(array) {
      let currentIndex = array.length,
        randomIndex;
      while (currentIndex != 0) {
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex--;
        [array[currentIndex], array[randomIndex]] = [
          array[randomIndex],
          array[currentIndex],
        ];
      }

      return array;
    },
  },
};
</script>

<style scoped>
.main-second {
  display: flex;
  justify-content: center;
  align-items: center;
}
.main-container {
  width: 70%;
  min-height: 100vh;
  padding: 50px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
.question {
  padding: 10px;
  width: 50%;
  height: 35px;
  background: rgb(41, 102, 194);
  color: white;
  font-weight: 700;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.answers {
  padding: 10px;
  width: 50%;
  height: 25px;
  background: rgb(166, 197, 243);
  color: black;
  font-weight: 700;
  margin: 10px 0;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.answers:hover {
  background: rgb(204, 219, 241);
  color: rgb(19, 15, 15);
  cursor: pointer;
}
</style>
