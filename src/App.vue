<template>
  <div id="app">

    <h1>Would you rather??</h1>
<!--component from other vue file-->
    <would-you-rather v-for="question in questions"
    v-bind:id="question.id"
    v-bind:question="question.wyrQuestion"
    v-bind:answer1="question.wyrAnswer1"
    v-bind:answer2="question.wyrAnswer2"
    v-on:answer-changed="answerChanged"
    >
    </would-you-rather>
<!--display user's choices-->
      <h3 v-show="isContent"> your choices are... </h3>
      <ul id="user-choices-list">
    <li v-for="userAnswer in userSelectedMessage" :key="userSelectedMessage">{{userAnswer}}</li>
      </ul>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
        questions: [
            {
                id: 0,
                wyrQuestion: "Would you rather have an elephant-sized cat or a cat-sized elephant?",
                wyrAnswer1: "Elephant-sized cat",
                wyrAnswer2: "Cat-sized elephant",
            },
            {
                id: 1,
                wyrQuestion: "Would you rather taste the best pizza that has ever existed once but never again or have the 4th best pizza restaurant in the world within delivery distance?",
                wyrAnswer1: "Best pizza ever, once",
                wyrAnswer2: "Close pizza, no restrictions",
            },
            {
                id: 2,
                wyrQuestion: "Would you rather eat broccoli flavored ice cream or meat flavored cookies?",
                wyrAnswer1: "Broccoli flavored ice cream",
                wyrAnswer2: "Meat flavored cookies",
            },
        ],
        userSelectedMessage: [],
        isContent: false //bool to help show results header
    }
  },
    //detects a choice is made or changed, changes the value of UserSelectedMessage array
  methods: {
    answerChanged(choice, id) {
        this.$set(this.userSelectedMessage, id, choice);
        this.isContent = true
    }
  }
}
</script>

<style>

body {
  background: violet;
}

#user-choices-list {
    font-size: 28px;
}
h3 {
    font-style: italic;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: aqua;
}
</style>
