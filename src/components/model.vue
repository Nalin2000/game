<template>
  <transition name="modal">
    <div class="modal-mask content">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">
              <h3>Please Start</h3>
            </slot>
          </div>

          <div class="modal-body">
            <slot name="body"></slot>

            <slot name="footer">
              <button
                class="button-a mt-5"
                id="new"
                @click="$emit('close',false),$emit('reset',0),$emit('$reset','')"
              >New Game</button>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "modal",
  props: {
    lable: String,
  },
  data: function () {
    return {
      showModal: false,
    };
  },
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 80%;
  height: 80%;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: rgba(0, 0, 0, 0.911);
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header h3 {
  margin-top: 0;
  color: #ffffff;
}

.modal-body {
  margin: 190px 0;
}

.modal-header {
  color: #ffffff;
}

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

.button-a {
  background-color: rgb(174, 206, 255);
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 10px 3px;
  font-size: 2vw;
  cursor: pointer;
  border-radius: 100px;
  border: 0.5px solid rgb(42, 5, 250);
  width: 30vw;
}

button:hover#new {
  color: #2f00ffbe;
  border: 0.5px solid black;
  background-color: black;
}
</style>