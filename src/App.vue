<template>
  <!--bag image -->
  <div id="bag" :class="{burst: ended}">

  </div>
  <!--bag health -->
  <div id="bag-health">
    <div :style="{width: health+'%'}"></div>
  </div>
  <!--game control -->
  <div id="controls">
    <button @click="punch" v-if="!ended">Punch</button>
    <div class="divider"></div>
    <button @click="restart">Restart</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      health: 100,
      ended: false
    }
  },
  methods: {
    punch(){
      this.health -= 10
      if (this.health <= 0){
        this.ended = true
      }
    },
    restart(){
      this.health = 100
      this.ended = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#bag{
  width: 200px;
  height: 500px;
  margin: 0 auto;
  background: url('./assets/bag.png') center no-repeat;
  background-size: 80%
}
#bag.burst{
  background: url('./assets/bag-burst.png') center no-repeat;
  background-size: 80%
}
#bag-health{
  width: 200px;
  border: 2px solid #000;
  margin: 0 auto 20px auto;
}
#bag-health div{
  height: 20px;
  background: crimson;
}
#controls{
  width: 120px;
  margin: 0 auto;
}
button{
  color: black;
  transition-duration: 0.4s;
  border-radius: 10px;
  padding: 6px;
}

button:hover {
  background-color: black;
  color: white;
  border: 2px solid white;
}
.divider{
  width: 5px;
  height: auto;
  display: inline-block;
}
</style>
