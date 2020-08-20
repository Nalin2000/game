<template>
  <div>
    <div class="a">
      <hr />
      name = {{aPlayer.name}}
      hp = {{aPlayer.hp}}
      image = {{aPlayer.image}}
      attack = {{this.randomNO(3,10)}}
      <hr />
      name = {{bMonster.name}}
      hp = {{bMonster.hp}}
      image = {{bMonster.image}}
      attack = {{this.randomNO(3,10)}}
    </div>
    <!-- {{player[randomNO(1,3)-1].name}}
    ได้ทั้งชื่อและ hp ออกมา
    {{randomDamage(1,300)}} สุ่ม 1 - 300-->
    <button v-on:click="$start" class="button-a" id="yellow">START</button>
    <button v-on:click="$attack" class="button-a" id="purple">ATTACK</button>
    <button v-on:click="$special" class="button-a" id="purple">SPECIAL</button>
  </div>
</template>


<script>
export default {
  data: function () {
    return {
      //เอาชื่อออกจาก object player[1].name
      //เอาชื่อออกจาก object player[random].name
      aPlayer: { name: "", hp: 0, image: "" },
      bMonster: { name: "", hp: 0, image: "" },
      special: 0,
      player: [
        { name: "Anakin", hp: 90, image: "a" },
        { name: "Ironman", hp: 150, image: "b" },
        { name: "Doreamon", hp: 200, image: "c" },
      ],
      monster: [
        { name: "Thanos", hp: 90, image: "x" },
        { name: "Darth", hp: 10, image: "y" },
        { name: "Comti", hp: 20, image: "z" },
      ],
    };
  },

  methods: {
    randomNO: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    $start: function () {
      //1.random Plaryer 1-3 -->ชื่อ ค่า hp รูป ฝากไว้ใน aPlary
      this.aPlayer = this.player[this.randomNO(1, 3) - 1];
      //2.random Monster 1-3
       this.bMonster = this.monster[this.randomNO(1, 3) - 1];
    },
    $attack: function () {
      // p -> mon
      this.attackP = this.randomNO(3,10);

      // p <- mon
      //p <=0 ===ทำไง  you lose
      //mon <==0 ทำไง you win
      //End
    },
    $special: function () {},
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
  margin: 4px 2px;
  font-size: 50px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid white;
  width: 300px;
}
.button-a-font-dd {
  background-color: white;
  border: none;
  color: #646363;
  padding: 5px 5px 5px 5px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid #ffffff;
  width: 300px;
}

button:hover#yellow {
  color: #ffcc66;
}
button:hover#purple {
  color: #9370db;
}
.a {
  margin: auto;
  width: 70%;
  height: 500px;
  border: 10px solid black;
}
</style>