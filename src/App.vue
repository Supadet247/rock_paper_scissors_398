<template>
  <div id="app">
    <div class="text-border-radius">
      <h1>Rock Paper Scissors</h1>
    </div>
    
    <GameComponent />
  </div>
</template>

<script>
import GameComponent from './components/game.vue';

export default {
  components: {
    GameComponent,
  },
};
</script>

<style>
#app {
  text-align: center;
  color: #e7e6e6;
  margin-top: 0px;
  background-color: #000000;
  width: 70%;
  height: 110vh;
  display: flex;
  flex-direction: column;
}


.text-border-radius {
  border: 2px solid #f6f4f4;
  padding: 5px;
  border-radius: 10px; 
}

.player1-name {
  color: #111dff; 
}
.player2-name {
  color: #ff3730; 
}


.player-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  
}

.reset-button {
  margin-left: 70px; 
  background-color: #00a957; 
  color: #fff; 
  border-radius: 5px; 
}

.reset-button:hover {
  background-color: #008c47; 
}
.round-button:hover {
  background-color: #b10202ee; 
}

.round-button {
  
  background-color: #e70707; 
  color: #fff;
  border-radius: 5px; 
}

.score-container {
  background-color: #ffffff; 
  color: #000000; 
  padding: 3px; 
  margin-top: 15px; 
  text-align: center; 
  border-radius: 15px; 
  border: 2px solid #e8e8e7; 
  max-width: 300px; 
  margin: 15px auto;
}

.score-text {
  margin: 0; 
}
</style>




