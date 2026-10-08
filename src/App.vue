<script setup lang="ts">
import { ref } from 'vue';
var score = ref(0);
var src = ref("/images/vache.jpeg");
var an= ["/images/lion.jpeg","/images/ours.jpeg","/images/daulphan.jpeg","/images/lapin.jpeg",""];
var rep=[2,1,3,1,2];
var k=0;
var dis=ref(false);
var pr = ref(1)
function verif(x) {
  dis.value=!dis.value;
  if (x==rep[k]) {
    score.value++;
  }
}
function suivant(){
  if (pr.value<5) {
    pr.value++;
  }
  src.value=an[k];
  dis.value=!dis.value;
  k++;
}
function reset(){
  k=0;
  pr.value=1;
  score.value=0;
  src.value="/images/vache.jpeg";

}


</script>

<template>
<header>
  <h1>Animaux Quiz</h1>
  <span>Votre score : {{ score }}</span>
</header>
<body>
  <div><img :src="src" alt=""></div>
  <div v-if="k<5" ><ul><li><input id="b1" type="button" value="1. 🥩 De la viande" @click="verif(1)" :disabled="dis"></li> 
    <li><input id="b1" type="button" value="2. 🌿 Des plantes" @click="verif(2)" :disabled="dis"></li>
    <li><input id="b2" type="button" value="3. 🥩🌿 Les deux" @click="verif(3)" :disabled="dis"></li></ul></div>
    <div ><input id="b3" type="button" value="Suivant" :disabled="!dis" @click="suivant()" v-if="k<5">
          <input type="button" value="Rejouer" v-else @click="reset()"></div>
</body>
<footer>
  <div><input type="range" name="" id="rang" max="5" readonly :value="pr" ></div>
  <div><p><span>{{ pr }}</span>/5</p></div>
</footer>
</template>

<style scoped>
header {
  background-color: #4CAF50;
  color: white;
  padding: 15px;
  text-align: center;
  font-family: Arial, sans-serif;
}
body {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
  font-family: Arial, sans-serif;
}
img {
  max-width: 300px;
  border: 3px solid #4CAF50;
  border-radius: 10px;
  margin-bottom: 20px;
}
ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 10px 0;
}
input[type="button"] {
  background-color: #f0f0f0;
  border: 2px solid #4CAF50;
  border-radius: 5px;
  padding: 10px 15px;
  cursor: pointer;
  font-size: 14px;
}

input[type="button"]:hover {
  background-color: #4CAF50;
  color: white;
}

input[type="button"]:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
footer {
  margin-top: 20px;
  text-align: center;
}
</style>
