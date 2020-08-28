<template>
  <div>
    <button @click="randomStart()" class="btn btn-danger btn-lg mb-2">Start</button>
    <div class="row">
      <div class="col">
        <button @click="randomDamage(3,10)" class="btn btn-primary mb-4">Attack</button> 
        <button @click="randomDamageSP(10,20)" class="btn btn-info mb-4">Ultimate  Attack</button> 
      </div>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="col">
          <div class="alert alert-primary" role="alert">Character : {{randomPlayer}} HP : {{hp1}}</div> 
          <img :src="image1" class="img-fluid" />
        </div>
        <div class="col">
          <div class="alert alert-primary" role="alert">Character : {{randomMonster}} HP : {{hp2}}</div> 
          <img :src="image2" class="img-fluid" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomAttack: "",
      randomSpAttack: "",
      image1: "",
      image2: "",
      hp1: "",
      hp2: "",
      win: "./assets/win.png", 
      lose: "./assets/lose.png", 
      player: [
        {
          name: "Ironman", 
          hp: 160, 
          image: "./assets/ironman.png" 
        },
        {
          name: "captain america", 
          hp: 160, 
          image: "./assets/cap.png", 
        },
        {
          name: "Thor", 
          hp: 200, 
          image: "./assets/thor.png", 
        },
      ],
      randomPlayer: "",
      monster: [
        {
          name: "Loki", 
          hp: 150, 
          image: "./assets/lokii.png", 
        },
        {
          name: "Hela", 
          hp: 170,
          image: "./assets/helaa.png", 
        },
        {
          name: "Thanos", 
          hp: 200, 
          image: "./assets/thanos.png", 
        },
      ],
      randomMonster: "",
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[chosenNumber1].name;
      this.hp1 = this.player[chosenNumber1].hp;
      this.image1 = this.player[chosenNumber1].image;

      var chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[chosenNumber2].name;
      this.hp2 = this.monster[chosenNumber2].hp;
      this.image2 = this.monster[chosenNumber2].image;
    },

    randomDamage: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp1 -= this.randomAttack;
      }
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },

    randomDamageSP: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },
  },
};
</script>

<style>
</style>