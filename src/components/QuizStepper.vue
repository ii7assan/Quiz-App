<template>
  <v-stepper v-model="e1">
    <v-stepper-header>
      <v-stepper-step
        v-for="(q, i) in question"
        :key="i"
        :complete="e1 > i"
        step="i"
      >
        Question {{ i + 1 }}
      </v-stepper-step>
    </v-stepper-header>

    <v-stepper-items v-for="(x, index) in question" :key="index">
      <v-stepper-content :step="index + 1">
        <h3 class="pa-5 headline">
          {{ x.question }}
        </h3>
        <v-card
          class="mb-10 pa-4 display-1 rounded-lg"
          color=" lighten-1"
          height="200px"
        >
          <v-row justify="space-around">
            <v-radio-group
              class="pa-1"
              v-for="answer in x.answers"
              :key="answer"
              @change="selectedAnswer($event, index)"
              v-model="radioGroup"
            >
              <v-radio :key="index" :label="answer" :value="answer"></v-radio>
            </v-radio-group>
          </v-row>
        </v-card>
        <v-btn color="primary" @click="nextStep()"> Next </v-btn>
      </v-stepper-content>
    </v-stepper-items>
    <ScoreModal
      :dialog="isLastStep"
      :totalScore="totalScores"
      :questionsLenght="questionLength"
    />
  </v-stepper>
</template>

<script>
import ScoreModal from "./ScoreModal.vue";
export default {
  components: { ScoreModal },
  props: {
    question: Array,
  },
  data: () => ({
    e1: 1,
    radioGroup: 1,
    score: 0,
    scores: [],
  }),
  computed: {
    isLastStep() {
      return this.e1 == this.question.length + 1 ? true : false;
    },
    totalScores() {
      return this.scores.reduce((acc, cur) => acc + cur, 0);
    },
    questionLength() {
      return this.question.length;
    },
  },
  mounted() {
    setInterval(() => {
      if (this.isLastStep) {
        this.e1 = 1;
      }
    }, 10000);
  },
  methods: {
    selectedAnswer(event, index) {
      if (event === this.question[index].correctAnswer) {
        this.score++;
        this.addScore(this.score);
      } else {
        if (this.question[index]) {
          this.score = 0;
          this.scores.splice(index, 1);
        }
      }
    },
    addScore(score) {
      this.scores.push(score);
      this.score = 0;
    },
    nextStep() {
      this.e1 += 1;
      this.radioGroup = 0;
    },
  },
};
</script>

<style>
</style>