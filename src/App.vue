<template>
  <div id="app">
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

    <div class="a">
      <div class="row">
        <div class="col-md-4 col-sm-4">
          <h1>{{he_name}}</h1>
            <b-progress
            :value="he_hp"
            :max="max"
            class="bar"
            show-value
            variant="success"
            show-progress
            animated
          ></b-progress>
          <div class="tile">
            <img :src="h_img" alt class="img-fluid image" :width="he_hp + 'px'" />
          </div>
          
        </div>
        <div class="col-md-4 mt-5 col-sm-4">
          <img src="./assets/img/vs1.png" />
        </div>
        <div class="col-md-4 col-sm-4">
          <h1>{{mon_name}}</h1>
          <b-progress
            :value="mon_hp"
            :max="max"
            class="bar"
            show-progress
            show-value
            variant="danger"
            animated
          ></b-progress>
          <div class="tile">
            <img :src="m_img" class="img-fluid image" :width=" mon_hp + 'px'" />
          </div>
        </div>
      </div>
    </div>

 

    <modal
      v-if="he_hp <= 0 && mon_hp > 0 && he_name != ''"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">YOU LOUSE</h1>
    </modal>

    <modal
      v-if="mon_hp <= 0 && he_hp > 0 && he_name != ''"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">YOU WIN</h1>
    </modal>

    <modal
      v-if="(he_hp<=0 && mon_hp <= 0 ) && he_name != ''"
      v-bind="reset"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">DRAW</h1>
    </modal>
  </div>
</template>

<script>
import infinity from "./components/infinity";
import modal from "./components/model";
export default {
  name: "App",
  components: {
    modal,
    infinity,
  },
  data: function () {
    return {
      he_name: "",
      mon_name: "",
      he_hp: 0,
      mon_hp: 0,
      max_h: 0,
      attack: 0,
      h_img: "",
      m_img: "",
    };
  },
  methods: {
    //HERO
    h_name(value) {
      this.he_name = value;
    },
    h_hp(value) {
      this.he_hp = value;
      this.max1 = value;
    },
    h_image(value) {
      this.h_img = value;
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
    $reset(value) {
      this.he_name = value;
      this.mon_name = value;
      this.h_img = value;
      this.m_img = value;
    },
    reset(value) {
      this.he_hp = value;
      this.mon_hp = value;
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
.bar {
  height: 25px;
  border-radius: 20px;
}
</style>
