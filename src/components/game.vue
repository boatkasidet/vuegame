<template class="container-fluid ">
  <div>
    <div class="cardtop display-2">VUE-GAME</div>
    
    <!-- game -->
    <div>
      <div class="row">
        <div class="col-4">
          <p class="display-4 bg-white">NAME : {{randomPlayer}}</p>
          <p
            class="display-4 progress-bar progress-bar-striped progress-bar-animated bg-danger"
          >HP : {{hp1}}</p>
          <img :src="image1" />
        </div>

        <div class="col-4">
          <!-- win -->
          <p v-if="hp1 <= -1 ">
            <br />
            <img
              src="https://media0.giphy.com/media/H1jVdqPuTsmoV9xwmH/giphy.gif"
              height="300"
              width="300"
            />
          </p>
          <!-- lose -->
          <p v-else-if="hp2 <= -1 ">
            <br />
            <img
              src="https://media2.giphy.com/media/xULW8CPwOHXPua8NTa/source.gif"
              height="300"
              width="300"
            />
          </p>
          <!-- VS -->
          <p v-else>
            <br />
            <img
              src="https://media0.giphy.com/media/3Fie42HOj3uwIX3YNv/giphy.gif"
              height="400"
              width="400"
            />
          </p>
        </div>

        <div class="col-4">
          <p class="display-4 bg-white">NAME : {{randomMonster}}</p>
          <p class="display-4 progress-bar progress-bar-striped progress-bar-animated bg-danger">HP : {{hp2}}</p>
          <img :src="image2" />
        </div>
      </div>
    </div>

    <!-- Button -->
    <bt class="fixed-bottom">
      <div>
        <button @click="randomStart()" class="button btn-success">Start{{Label}}</button>
      </div>
      <br />
      <div class="row">
        <div class="col-12">
          <button @click="randomDamage()" class="button btn-warning ml-3">Attack{{Label}}</button>
          <button @click="randomSpDamage()" class="button btn-danger ml-3">Special Attack{{Label}}</button>
        </div>
      </div>
    </bt>
  </div>
</template>

<script>
//game
export default {
  data: function () {
    return {
      randomPlayerAttack: "",
      randomMonsterAttack: "",
      randomSpAttack: "",
      image1: "",
      image2: "",
      hp1: " ",
      hp2: " ",

      player: [
        {
          name: "TORIKO",
          hp: 200,
          image:
            "https://4.bp.blogspot.com/-PgV51p2NT8A/UtbSQj2ejxI/AAAAAAAAAkQ/6GS7S9b8h1w/s1600/200px-Toriko_US.png",
        },
        {
          name: "SANY",
          hp: 170,
          image:
            "https://1.bp.blogspot.com/-Wj2wgBIQBCY/UtbWE6_Fy2I/AAAAAAAAAkg/sMooldkhpn4/s1600/200px-Sunny_GGB.png",
        },
        {
          name: "COCO",
          hp: 190,
          image:
            "https://sites.google.com/site/tangmaygeo/_/rsrc/1472760513415/4ctur-theph/toriko-Coco.gif?height=400&width=171",
        },
        {
          name: "ZEBRA",
          hp: 180,
          image:
            "https://2.bp.blogspot.com/-PoaT6NBOxp0/UtbXm56SipI/AAAAAAAAAko/L7QUKUpkiuk/s1600/290px-Zebra_GM.png",
        },
      ],
      randomPlayer: "",
      
      monster: [
        {
          name: "GT ROBO",
          hp: 230,
          image:
            "https://vignette.wikia.nocookie.net/toriko/images/7/74/GT_Robo..png/revision/latest/scale-to-width-down/340?cb=20130322161611",
        },
        {
          name: "MIDORA",
          hp: 250,
          image:
            "https://vignette.wikia.nocookie.net/toriko/images/9/91/Midora_GGB.png/revision/latest/scale-to-width-down/340?cb=20130703165207",
        },
        {
          name: "NITRO",
          hp: 220,
          image:
            "https://vignette.wikia.nocookie.net/toriko/images/2/2b/Nitro_GGB.png/revision/latest/scale-to-width-down/340?cb=20130703163043",
        },
        {
          name: "ALFARO",
          hp: 210,
          image:
            "https://vignette.wikia.nocookie.net/toriko/images/9/9a/Alfaro._GGB.png/revision/latest/scale-to-width-down/340?cb=20130703164937",
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

    randomDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 10) + 1, 3);
      this.hp2 -= this.randomPlayerAttack;

      this.randomMonsterAttack = Math.max(
        Math.floor(Math.random() * 15) + 1,
        5
      );
      this.hp1 -= this.randomMonsterAttack;
    },

    randomSpDamage: function () {
      this.randomPlayerAttack = Math.max(
        Math.floor(Math.random() * 20) + 1,
        10
      );
      this.hp2 -= this.randomPlayerAttack;

      this.randomMonsterAttack = Math.max(
        Math.floor(Math.random() * 15) + 1,
        5
      );
      this.hp1 -= this.randomMonsterAttack;
    },
  },
};
</script>

<style>
.button {
  display: inline-block;
  padding: 15px 25px;
  font-size: 24px;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
  outline: none;
  color: #fff;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #999;
}

.button:active {
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}
</style>