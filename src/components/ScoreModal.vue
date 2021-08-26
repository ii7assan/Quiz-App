<template>
  <div class="text-center">
    <v-dialog :value="dialog" width="700">
      <v-card>
        <v-card-title class="text-h5 grey lighten-2"> Score </v-card-title>

        <v-card-text> your score is {{ totalScore }} / {{questionsLenght}} </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="dialog = false"> exit </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  props: {
    dialog: Boolean,
    totalScore: Number,
    questionsLenght: Number
  },
};
</script>

<style>
</style>