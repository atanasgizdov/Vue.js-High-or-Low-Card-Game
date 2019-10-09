<template>
  <div id="app" class="small-container">
    <h1>Card Game - Guess the number!</h1>
    <div v-if = "cardValues.gameRunning == true">
      <button class = "button" v-on:click="submitGuess(2)"> The number is Even</button>
      <button class = "button" v-on:click="submitGuess(1)"> The number is Odd </button>
    </div>
    <div v-else>
      <button v-on:click="restartGame()">Play Again</button>
    </div>
    <Card :cardValues="cardValues"/>
    <br>


  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'app',
  components: {
    Card
  },
  data() {
    return {
      cardValues:
        {
        gameRunning: true,
        numberOfWins: 0,
        cardValue: Math.floor(Math.random() * Math.floor(11)),
        cardMessage: null
        },
    }
  },
  methods: {

    submitGuess: function (selection) {
      console.log ((this.cardValues.cardValue % 2))
      if (selection == 1 && ((this.cardValues.cardValue % 2) > 0)) {
        this.cardValues.cardMessage = "Congrats! You guessed correctly!"
        this.cardValues.numberOfWins++
      }
      else if (selection == 2 && ((this.cardValues.cardValue % 2) == 0)) {
        this.cardValues.cardMessage = "Congrats! You guessed correctly!"
        this.cardValues.numberOfWins++
      }
      else {
        this.cardValues.cardMessage = "Sorry, you did not guess correctly"
      }
      this.cardValues.gameRunning = false;
    },

    restartGame: function () {
      this.cardValues.gameRunning = true
      this.cardValues.cardValue = Math.floor(Math.random() * Math.floor(11))
    },

  }
}
</script>

<style>
.small-container {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  width: 40%;
  display: block;
  margin-left: auto;
  margin-right: auto;
  text-align: center;

}

.button {
  margin-left: 5px;
  margin-right: 5px;
}
</style>
