<template>
  <div>
    <div class="player-container">
      <div>
        <h2 class="player-name">Player 1</h2>
        <div class="choice">
          <img class="small-image" :src="getPlayerImage(player1Choice)" :alt="player1Choice" />
          <h3>Choose:</h3> {{ player1Choice }}
          <h3>Result:</h3> {{ gameResult1 }}
        </div>
      </div>

      <div>
        <h2 class="player-name">Player 2</h2>
        <div class="choice">
          <img class="small-image" :src="getPlayerImage(player2Choice)" :alt="player2Choice" />
          <h3>Choose:</h3> {{ player2Choice }}
          <h3>Result:</h3> {{ gameResult2 }}
        </div>
      </div>
    </div>

    <div>
      <button @click="playRound" class="round-button">Play</button>
      <button @click="resetGame" class="reset-button">Replay</button>
    </div>

    <div class="score-container">
      <h2 class="score-text">Point {{ player1Score }} : {{ player2Score }}</h2>
    </div>
  </div>
</template>

<style>
img {
  width: 100px;
  height: auto;
}

.choice {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.player-container {
  display: flex;
  justify-content: space-between;
}

.player-name {
  text-align: center;
}

.score-container {
  text-align: center;
}
</style>

<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      player1Score: 0,
      player2Score: 0,
      gameResult1: '',
      gameResult2: '',
      player1Choice: '',
      player2Choice: '',
      choices: ['Rock', 'Paper', 'Scissors'],
      playerImages: {
        Rock: 'src/assets/rk_L.png',
        Paper: 'src/assets/pp_L.png',
        Scissors: 'src/assets/sc_L.png',
      },
    };
  },
  methods: {
    getPlayerImage(choice) {
      return this.playerImages[choice];
    },
    playRound() {
      const player1Index = Math.floor(Math.random() * this.choices.length);
      const player2Index = Math.floor(Math.random() * this.choices.length);

      const player1Choice = this.choices[player1Index];
      const player2Choice = this.choices[player2Index];

      if (player1Choice === player2Choice) {
        this.gameResult1 = 'Draw';
        this.gameResult2 = 'Draw';
      } else if (
        (player1Choice === 'Rock' && player2Choice === 'Scissors') ||
        (player1Choice === 'Paper' && player2Choice === 'Rock') ||
        (player1Choice === 'Scissors' && player2Choice === 'Paper')
      ) {
        this.gameResult1 = 'Win';
        this.gameResult2 = 'Lose';
        this.player1Score++;
      } else if (
        (player1Choice === 'Scissors' && player2Choice === 'Rock') ||
        (player1Choice === 'Rock' && player2Choice === 'Paper') ||
        (player1Choice === 'Paper' && player2Choice === 'Scissors')
      ) {
        this.gameResult1 = 'Lose';
        this.gameResult2 = 'Win';
        this.player2Score++;
      }
      this.player1Choice = player1Choice;
      this.player2Choice = player2Choice;
    },
    resetGame() {
      this.player1Score = 0;
      this.player2Score = 0;
      this.gameResult1 = '';
      this.gameResult2 = '';
      this.player1Choice = '';
      this.player2Choice = '';
    },
  },
};
</script>
