<template>
  <div>
    <!-- <v-container fluid>
      <v-row v-for="(question,i) in questions" :key="question.question">
        {{question.question}}
        <v-col justify="center" align="center" v-for="(answer) in question.answers" :key="answer">
          <v-radio-group @change="selected($event,i)" v-model="radioGroup">
            <v-radio
              :key="i"
              :label="answer"
              :value="answer"
            ></v-radio>
          </v-radio-group>
        </v-col>
      </v-row>
    </v-container> -->
    <div id="app">
  <v-app id="inspire">
    <v-stepper v-model="e1" >
      <v-stepper-header >
        <v-stepper-step v-for="(q,i) in questions" :key="i"
          :complete="e1 > i+1"
          step="i"
        >
          Name of step {{i+1}}
        </v-stepper-step>
      </v-stepper-header>
  
      <v-stepper-items v-for="(x,index) in questions" :key="index">
        <v-stepper-content   :step="index+1">
          <v-card
            class="mb-12 display-1"
            color="grey lighten-1"
            height="200px"
          >{{index+1}}</v-card>
  
          <v-btn
            color="primary"
            @click="e1 += 1"
          >
            Continue
          </v-btn>
  
          <v-btn text>
            Cancel
          </v-btn>
        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>
  </v-app>
</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radioGroup: 1,
      e1:1,
      questions: [
        {
          question: "what my age? ",
          answers: ['18','19','20','21'],
          correctAnswer: '20'
        },
        {
          question: "what my name? ",
          answers: ['ahmad','hassan','jafar','ali'],
          correctAnswer: 'hassan'
        },
        {
          question: "what my sex? ",
          answers: ['female','male'],
          correctAnswer: 'male'
        },
      ],
      score: 0,
    };
  },
  methods: {
    selected(event,index) {
      if(event === this.questions[index].correctAnswer){
        console.log('correct',event)
        this.score++
      }else{
      console.log('no correct',event);
      }
    },
  },
  mounted(){
  }
};
</script>

<style>
</style>