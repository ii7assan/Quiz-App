<template>
  <div>
    <quiz-stepper :question="questions" />
  </div>
</template>

<script>
import QuizStepper from './QuizStepper.vue';
export default {
  components: { QuizStepper },
  data() {
    return {
      radioGroup: 1,
      e1: 1,
      questions: [
        {
          question: "what my age? ",
          answers: ["18", "19", "20", "21"],
          correctAnswer: "20",
        },
        {
          question: "what my name? ",
          answers: ["ahmad", "hassan", "jafar", "ali"],
          correctAnswer: "hassan",
        },
        {
          question: "what my sex? ",
          answers: ["female", "male"],
          correctAnswer: "male",
        },
         {
          question: "what my sex ",
          answers: ["female", "male"],
          correctAnswer: "male",
        },
      ],
      score: 0,
    };
  },
  
};
</script>

<style>
</style>