<template>
  <div class="p-3 text-gray-500 text-sm leading-tight selection:text-gray-700">
    <h1 class=" text-gray-400">Fabian Beier</h1>
    <p>Design / Development</p>
    <a href="mailto:mail@fabian-beier.de" class="text-gray-600">mail@fabian-beier.de</a>
    <client-only >
    <input type="text" v-model="number">
     <Renderer ref="renderer" antialias resize="window" orbit-ctrl >
    <Camera :position="{ z: 4 }"></Camera>
    <Scene>
      <PointLight :position="{ y: 10, z: 10 }"></PointLight>
      <Box ref="box" @click="boxClick"  :rotation="{ y: number, z: single, x: single }" v-for="single in amount" :key="single">
        <LambertMaterial></LambertMaterial>
      </Box>
    </Scene>
  </Renderer>
  </client-only>
  </div>
</template>

<script>
import { Box, Camera, LambertMaterial, PointLight, Renderer, Scene } from 'troisjs';

export default {
  components: { Box, Camera, LambertMaterial, PointLight, Renderer, Scene },
  data() {
    return {
      number: 1,
      amount: 3
    }
  },
 methods: {
    boxOver({ over }) {
      this.boxColor = over ? '#ff0000' : '#ffffff';
    },
    boxClick(e) {
      alert('Click');
      console.log(e);
    },
    looperMove() {
      var that = this;
       setInterval(function name() {
         that.number += 0.01
       }, 10);
    }
  },
  mounted () {
    this.looperMove()
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Space+Mono&display=swap');



body{
  font-family: 'Space Mono', monospace;
}

body{
  @apply bg-gray-800
}

canvas{
  @apply fixed top-0 left-0 z-[-1]
}

</style>
