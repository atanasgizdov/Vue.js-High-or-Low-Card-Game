<template>
  <div class="card">
    <img v-if= "cardValues.gameRunning == true" src="https://i.imgur.com/TC1UgEj.jpg" alt="Avatar" style="width:100%">
    <div v-else class="container">
      <h4><b> {{ cardValues.cardMessage }}</b></h4>
      <h4><b>The value of the card was : {{ cardValues.cardValue }}</b></h4>
      <h5>You have won a total number of <b> {{ cardValues.numberOfWins }}</b> times</h5>
      <p>Click play again to restart the game</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'card-class',
    props: {
      cardValues: Object
    },
  }
</script>



<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  width: 60%;
  display: block;
  margin-left: auto;
  margin-right: auto;

}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

.container {
  padding: 2px 16px;
}

</style>
