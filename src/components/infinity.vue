<template>
  <div>
    <!-- {{player[randomNO(1,3)-1].name}}
    ได้ทั้งชื่อและ hp ออกมา
    {{randomDamage(1,300)}} สุ่ม 1 - 300-->
    <button v-on:click="$start" class="button-a" id="start">START</button>
    <button v-on:click="$attack" class="button-a" id="atk">ATTACK</button>
    <button v-on:click="$special" class="button-a" id="atk">SPECIAL ATTACK</button>
  </div>
</template>


<script>
export default {
  data: function () {
    return {
      player: [
        {
          name: "Captain America",
          hp: 235,
          image: require("../assets/img/1CaptainAmerica.png"),
        },

        {
          name: "Captain Marvel",
          hp: 280,
          image: require("../assets/img/1_2CaptainMarvel.png"),
        },
        {
          name: "Hulk",
          hp: 240,
          image: require("../assets/img/1hulk.png"),
        },
        {
          name: "Ironman",
          hp: 250,
          image: require("../assets/img/1ironman.png"),
        },
        {
          name: "Thor",
          hp: 255,
          image: require("../assets/img/1Thor.png"),
        },
      ],

      monster: [
        {
          name: "Shazam",
          hp: 230,
          image: require("../assets/img/2Shazam.png"),
        },
        {
          name: "Halyquen",
          hp: 250,
          image: require("../assets/img/2Halyquen.png"),
        },
        {
          name: "Aquaman",
          hp: 240,
          image: require("../assets/img/2Aquaman.png"),
        },
        {
          name: "Thanos",
          hp: 260,
          image: require("../assets/img/2thanos.png"),
        },
        {
          name: "Wonder Woman",
          hp: 240,
          image: require("../assets/img/2_2wonder_woman.png"),
        },
      ],
    };
  },

  methods: {
    randomNO: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },

    $start: function () {
      //สร้าง random
      this.ranP = this.randomNO(1, 5) - 1;
      this.ranM = this.randomNO(1, 5) - 1;
      //1.random Plaryer 1-3 -->ชื่อ ค่า hp รูป
      this.name_Player = this.player[this.ranP].name;
      this.$emit("H_name", this.name_Player);

      this.hp_Player = this.player[this.ranP].hp;
      this.$emit("H_hp", this.hp_Player);

      this.image_Player = this.player[this.ranP].image;
      this.$emit("H_image", this.image_Player);

      //2.random Monster 1-3
      this.name_monster = this.monster[this.ranM].name;

      this.$emit("M_name", this.name_monster);
      this.hp_monster = this.monster[this.ranM].hp;
      this.$emit("M_hp", this.hp_monster);
      this.image_monster = this.monster[this.ranM].image;
      this.$emit("M_image", this.image_monster);
    },
    $attack: function () {
      // p -> mon
      this.atk = this.randomNO(3, 10);
      this.$emit("P_atk", this.atk);

      this.atk = this.randomNO(3, 10);
      this.$emit("M_atk", this.atk);
    },
    $special: function () {
      this.s_atk = this.randomNO(10, 20);
      this.$emit("P_SATK", this.s_atk);

      this.s_atk = this.randomNO(10, 20);
      this.$emit("M_SPATK", this.s_atk);
    },
  },
};
</script>

<style scoped>
.b {
  font-size: 50px;
}

.button-a {
  background-color: rgb(218, 204, 204);
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 10px 3px;
  font-size: 2vw;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid rgb(218, 204, 204);
  width: 30vw;
}

button:hover#start {
  color: red;
  background-color: black;
  border: 0.5px solid black;
}
button:hover#atk {
  color: #9370db;
  border: 0.5px solid black;
  background-color: black;
}
</style>