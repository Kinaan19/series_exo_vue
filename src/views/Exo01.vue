<template>
  <div id="Exo01">
    <h3 class="px-3" :class="{backgroundColor: x}">The background of this H tag is {{color}}</h3>
    <button class="btn" @click="changeColor">Change the color</button>
  </div>
</template>

<script>
export default {
  data(){
    return{
      color: "blue",
      x: false
    }
  },
  methods:{
    changeColor: function(){
      this.x = !this.x;
      if(this.x == true){
        this.color = "red";
      }else{
        this.color = "blue";
      }
    }
  }
}
</script>

<style scoped>
  h3{
    background-color: blue;
    width: 500px;
    height: 150px;
    margin: 0 auto 25px auto;
    line-height: 150px;
  }
  .backgroundColor{
    background-color: red;
  }
</style>


