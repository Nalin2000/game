<template>
  <div id="app">
    <div class="a">
      <div></div>
      <div class="row">
        <div class="col-md-4 col-sm-4">
          <h1>{{he_name}}</h1>
          <b-progress :value="he_hp" :max="max" show-progress animated></b-progress>
          <div class="heroTile tile">
            <img :src="h_img" alt class="img-fluid image" :width="he_hp + 'vw'" />
          </div>
        </div>
        <div class="col-md-4 mt-5 col-sm-4">
          <img src="./assets/img/vs1.png" />
        </div>
        <div class="col-md-4 col-sm-4">
          <h1>{{mon_name}}</h1>
          <b-progress :value="mon_hp" :max="max1" show-progress animated></b-progress>
          <div class="enemyTile tile">
            <img :src="m_img" class="img-fluid image" :width=" mon_hp + 'vw'" />
          </div>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12 col-sm-12">
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
    <div class="row">
      <div class="col-md-12">
        <div v-if="he_hp <= 0" class>
          You Louse
          Plaese Restart
        </div>
        <div v-if="mon_hp <= 0">
          You WIN
          Plaese Restart
        </div>

        <div v-if="mon_hp <= 0 && he_hp <= 0">
          Draw
          Plaese Restart
        </div>
      </div>
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
      this.max = this.he_hp;
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
      this.max1 = this.mon_hp;
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
  font-family: "Orbitron", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
}
.vs {
  margin-top: 20vw;
}
.a {
  margin: auto;
  width: 90%;
  height: 600px;
}
.con {
  width: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.tiles {
  position: absolute;
  bottom: 5%;
  width: 100%;
}

.tile {
  display: inline-block;
  margin: 5px;
  bottom: 0;
}

.heroTile {
  float: center;
}

.enemyTile {
  float: bottom;
}
</style>
