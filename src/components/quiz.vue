<template>
  <div>
    <v-container fluid>
      <v-row v-for="(quest,i) in questions" :key="quest.question">
        <v-col justify="center" align="center" v-for="(answer) in quest.answers" :key="answer">
          <v-radio-group @change="selected($event,i)" v-model="radioGroup">
            <v-radio
              :key="i"
              :label="answer"
              :value="answer"
            ></v-radio>
          </v-radio-group>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radioGroup: 1,
      questions: [
        {
          question: "what my age? ",
          answers: ['18','19','20','21'],
          correctAnswer: '20'
        },
      ],
    };
  },
  methods: {
    selected(event,index) {
      if(event === this.questions[index].correctAnswer){
        console.log('correct')
      }
      console.log(event);
    },
  },
};
</script>

<style>
</style>