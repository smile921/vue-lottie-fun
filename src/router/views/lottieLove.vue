<template>
  <layout>
    <div id="demo">
      <lottie 
        :options="defaultOptions" 
        :height="500" 
        :width="500" 
        @animCreated="handleAnimation"/>
      <div>
        <p>Speed: x{{ animationSpeed }}</p>
        <input 
          v-model="animationSpeed" 
          type="range" 
          value="1" 
          min="0" 
          max="3"
          step="0.5" 
          @change="onSpeedChange">
      </div>
      <button @click="stop">stop</button>
      <button @click="pause">pause</button>
      <button @click="play">play</button>
    </div>
  </layout>
</template>

<script>
import Lottie from '@src/components/lottie.vue'
import * as animationData from '@src/assets/animation-w100-h100.json'
import Layout from '@layouts/main'

export default {
  name: 'LottieLove',
  components: {
    lottie: Lottie,
    Layout,
  },
  data() {
    console.log(animationData.w)
    console.log(animationData.h)
    // debugger
    return {
      defaultOptions: { animationData: animationData },
      animationSpeed: 1,
    }
  },
  methods: {
    handleAnimation: function(anim) {
      this.anim = anim
    },

    stop: function() {
      this.anim.stop()
    },

    play: function() {
      this.anim.play()
    },

    pause: function() {
      this.anim.pause()
    },

    onSpeedChange: function() {
      this.anim.setSpeed(this.animationSpeed)
    },
  },
}
</script>

<style>
#demo {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
