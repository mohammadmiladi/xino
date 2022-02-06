<template>
  <div class="main-second">
    <div class="main-container">
      <div class="question">{{ questionsData[currentQuestion].question }}</div>
      <div class="timer">
        {{ timerCount }}
        <div id="progressBar">
          <div :style="`width: ${widthPercentage}%`" class="bar"></div>
          <div class="label"></div>
        </div>
      </div>
      <div
        v-for="(answerss, idx) in answers"
        :key="idx"
        @click="selectAnswer(answerss, idx)"
        class="answers"
      >
        {{ answerss.value }}
      </div>
      <div class="circles">
        <div
          :style="`background-color: ${circleColor[inx]}`"
          class="circle"
          v-for="(item, inx) in questionsData"
          :key="inx"
        ></div>
      </div>
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
      answers: [],
      currentQuestion: 0,
      timerCount: 0,
      widthPercentage: 0,
      circleColor: [],
    };
  },
  created() {
    this.questionsData = Questions;
    this.answers = this.shuffle(
      this.questionsData[this.currentQuestion].answers
    );
    this.timerCount = 10;
    this.countDown();
  },
  watch: {
    currentQuestion() {
      this.answers = this.shuffle(
        this.questionsData[this.currentQuestion].answers
      );
    },
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
    countDown() {
      setInterval(() => {
        if (this.timerCount > 0) {
          this.timerCount--;
          this.widthPercentage += 10;
        } else {
          if (this.questionsData.length == this.currentQuestion + 1) {
            this.$emit("changePage");
          } else {
            this.widthPercentage = 0;
            this.currentQuestion++;
            this.timerCount = 10;
          }
        }
      }, 1000);
    },
    selectAnswer(payload) {
      if (payload.answer) {
        this.circleColor[this.currentQuestion] = "green";
      } else {
        this.circleColor[this.currentQuestion] = "red";
      }
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
.circles {
  display: flex;
  justify-content: center;
  align-items: center;
}
.circle {
  border-radius: 50%;
  border: 1px solid gray;
  margin: 10px;
  width: 40px;
  height: 40px;
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
.timer {
  padding: 20px;
  background: rgb(224, 236, 255);
  box-shadow: 0 0 5px rgb(128, 128, 128);
  width: 100px;
  display: flex;
  font-weight: 700;
  flex-direction: column;
  margin: 20px 0;
  justify-content: center;
  align-items: center;
}
#progressBar {
  width: 100%;
  margin: 10px auto;
  height: 20px;
  background-color: #0a5f44;
  position: relative;
}

#progressBar .bar {
  height: 100%;
  text-align: right;
  padding: 0;
  line-height: 20px;
  width: 0;
  background-color: #cbea00;
  box-sizing: border-box;
  position: relative;
}

#progressBar .label {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%);
  color: #fff;
  font-size: 16px;
  height: 20px;
  display: inline-block;
  line-height: 20px;
}
.show-answer {
  margin-top: 10px;
  padding: 20px;
  border-radius: 7px;
}
.green-answer {
  background: rgb(181, 255, 181);
  color: green;
}
.red-answer {
  background: rgb(255, 223, 223);
  color: red;
}
</style>
