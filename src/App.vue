<template>
  <div id="app" class="playGameScreen">
<div>
  <div class="a">
    <div class="row">
      <div class="col-md-6">
      
        <h1>Hero : {{he_name}} | HP : {{he_hp}}</h1>
      </div>
      <div class="col-md-6">
        <h1>Monster : {{mon_name}} | HP : {{mon_hp}}</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-6">
        <img :src="h_img" alt class="img-fluid image" :width="he_hp + 'px'" />
      </div>
      <div class="col-md-6">
        <img :src="m_img" alt class="img-fluid image" :width=" mon_hp + 'px'" />
      </div>
    </div>
   </div> 
     <infinity
      @H_name="h_name"
      @H_hp="h_hp"
      @H_image="h_image"
      @M_name="m_name"
      @M_hp="m_hp"
      @M_image="m_image"
      @P_atk="p_atk"
      @M_atk="m_atk"
      @P_SATK="p_satk"
      @M_SPATK="m_satk"
    ></infinity>
   </div> 
  </div>
</template>

<script>
import infinity from "./components/infinity";
export default {
  name: "App",
  components: {
    infinity,
  },
  data: function () {
    return {
      he_name: "",
      mon_name: "",
      he_hp: 0,
      mon_hp: 0,
      attack: 0,
      h_img: "",
      m_img: "",
    };
  },
  methods: {
    //HERO
    h_name(value) {
      this.he_name = value;
      console.log("emit", this.he_name);
    },
    h_hp(value) {
      this.he_hp = value;
      console.log("emit", this.he_hp);
    },
    h_image(value) {
      this.h_img = value;
      console.log("emit", this.h_img);
    },
    //MONSTER
    m_name(value) {
      this.mon_name = value;
    },
    m_hp(value) {
      this.mon_hp = value;
    },
    m_image(value) {
      this.m_img = value;
    },
    //ATTACK HERO
    p_atk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
      console.log("emit", this.mon_hp);
    },
    p_satk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
    },
    //ATTACK MONSTER
    m_atk(value) {
      this.attack = value;
      this.he_hp -= this.attack;
    },
    m_satk(value) {
      this.attack = value;
      this.he_hp -= this.attack;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
}
.playGameScreen {
  background-image: url("assets/img/bg1.jpg");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}
.a {
    margin: auto;
  width: 70%;
  height: 500px;
  border: 10px solid black;
}
</style>
