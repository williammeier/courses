<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
      <result v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>

    <button
      type="button"
      v-if="this.questionsAnswered === questions.length"
      class="reset-btn"
      @click.prevent="reset"
    >
      Reset
    </button>
  </div>
</template>

<script>
import Questions from './components/Questions.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: 'What is 2 + 2?',
          answers: [
            {
              text: '4',
              is_correct: true,
            },
            {
              text: '3',
              is_correct: false,
            },
            {
              text: 'Fish',
              is_correct: false,
            },
            {
              text: '5',
              is_correct: false,
            },
          ],
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: '5',
              is_correct: false,
            },
            {
              text: '7',
              is_correct: false,
            },
            {
              text: '6',
              is_correct: true,
            },
            {
              text: '12',
              is_correct: false,
            },
          ],
        },
        {
          q: 'Find the missing letter: C_ke',
          answers: [
            {
              text: 'e',
              is_correct: false,
            },
            {
              text: 'a',
              is_correct: true,
            },
            {
              text: 'i',
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: 'Try again!',
          desc: 'Do a little more studying and you may succeed!',
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: 'Studying has definitely paid off for you!',
        },
      ],
    }
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++
      }

      this.questionsAnswered++
    },
    reset() {
      this.questionsAnswered = 0
      this.totalCorrect = 0
    },
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  font-size: 20px;
  font-family: sans-serif;
  padding-top: 20px;
  background: #e6ecf1;
}

.ctr {
  margin: 0 auto;
  max-width: 600px;
  width: 100%;
  box-sizing: border-box;
  position: relative;
}

.single-question {
  position: relative;
  width: 100%;
}

.fade-enter {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.3s linear;
}
.fade-leave-active {
  transition: all 0.3s linear;
  opacity: 0;
  position: absolute;
}

.reset-btn {
  background-color: #ff6372;
  border: 0;
  font-size: 22px;
  color: #fff;
  padding: 10px 25px;
  margin: 10px auto;
  display: block;
}
.reset-btn:active,
.reset-btn:focus,
.reset-btn:hover {
  border: 0;
  outline: 0;
}
</style>
