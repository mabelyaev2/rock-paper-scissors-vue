<template>
  <div id="app">
        <header class="game-header">
        <h1>Rock Paper Scissors Game</h1>
    </header>

    <main>
        <div class="game-score">
            <div class="game-score__user">
                <img src="./imgs/user-regular.png" alt="user-img">
            </div>
            <div class="game-score__board">
                <span id="user-score">{{ userScore }}</span>
                <span id="computer-score">{{ computerScore }}</span>
            </div>
            <div class="game-score__comp">
                <img src="./imgs/tv-solid.png" alt="comp-img">
            </div>
        </div>

        <div class="result">
            <p>{{ result }}</p>
        </div>

        <div class="user-choices">
            <div class="user-choice" id="rock" @click="FigureChoice('rock')">
                <img src="@/imgs/hand-rock-regular.svg" alt="hand-rock">
            </div>
            <div class="user-choice" id="paper" @click="FigureChoice('paper')">
                <img src="@/imgs/hand-paper-regular.svg" alt="hand-paper">
            </div>
            <div class="user-choice" id="scissors" @click="FigureChoice('scissors')">
                <img src="~@/imgs/hand-scissors-regular.svg" alt="hand-scissors">
            </div>
        </div>

        <p class="game-moves">Make your choice</p>
    </main>

  </div>
</template>

<script>
export default {
    data() {
      return {
        userScore: 0,
        computerScore: 0,
        result: '',
        userChoice: null,
        compChoice: null
      }
    },

    methods: {
     FigureChoice: function(choice) {
         this.userChoice = choice;
         const choices = ['rock', 'paper', 'scissors'];
         this.compChoice = choices[Math.floor(Math.random() * 3)];
         this.computedScore()
     },

     computedScore: function() {
         if (this.userChoice === 'rock') {
             if(this.compChoice === 'paper') {
                 this.result = 'Rock is beaten by Paper. You lost!';
                 this.computerScore++;
             } else if(this.compChoice === 'scissors') {
                 this.result = 'Rock beats scissors. You win!';
                 this.userScore++;
             } else if(this.compChoice === 'rock') {
                 this.result = 'Rock equals rock. It`s draw!';
             }
         }
         if(this.userChoice === 'paper') {
             if (this.compChoice === 'rock') {
                 this.result = 'Paper beats rock. You win!';
                 this.userScore++;
             } else if(this.compChoice === 'paper') {
                 this.result = 'Paper equals paper. It`s draw!';
             } else if(this.compChoice === 'scissors') {
                 this.result = 'Paper is beaten by scissors. You lost!';
                 this.computerScore++
             }
         }
         if(this.userChoice === 'scissors') {
             if(this.compChoice === 'rock') {
                 this.result = 'Scissors are beaten by rock. You lost!';
                 this.computerScore++;
             } else if(this.compChoice === 'paper') {
                 this.result = 'Scissors beat paper. You win!';
                 this.userScore++;
             } else if(this.compChoice === 'scissors') {
                 this.result = 'Scissors are equal to scissors. It`s draw!'
             }
         }
     }
    }
}
</script>

<style>
  body {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

h1, p, span {
    font-family: Helvetica, sans-serif;
    font-weight: bold;
    color: white;
}

.game-header > h1 {
    text-align: center;
    font-size: 30px;
    padding: 20px;
    color: black;
}

main {
    background-color: #2e3630;
    height: 100%;
    width: 100%;
    margin: 0;
}

.game-score {
    margin: 0 auto;
    padding-top: 20px;
    display: flex;
    flex-wrap: nowrap;
    justify-content: center;
}
.game-score__user,
.game-score__comp {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background-color: white;
    margin-top: 10px;
}

.game-score__user > img,
.game-score__comp > img  {
    width: 50px;
    height: 50px;
    display: flex;
    margin: 12px 15px;
}

.game-score__board {
    width: 180px;
    height: 100px;
    border: 3px solid white;
    border-radius: 5px;
    margin: auto 20px;
    text-align: center;
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.game-score__board > span {
    font-size: 66px;
}

.result > p {
    text-align: center;
    font-size: 40px;
    padding-top: 30px;
}

.user-choices {
    display: flex;
    flex-wrap: nowrap;
    justify-content: center;
    padding-top: 40px;
}

.user-choice {
    width: 180px;
    height: 180px;
    border-radius: 50%;
    background-color: #fff;
    margin-right: 35px;
}

.user-choice:hover {
    cursor: pointer;
}

.user-choice > img {
    width: 120px;
    height: 120px;
    margin: 25px 25px;
}

.game-moves {
    text-align: center;
    font-size: 35px;
    font-weight: bold;
    padding-bottom: 40px;
}
</style>
