
<template>
<div class="contenedor">
    <div class="titulo">

      <h1 id="tlr">PokeDes</h1>
    </div>

    <div class="for" style="text-align: center">
      <input class="caja" type="text" placeholder="Nombre o id del Pokemon" v-model="name" />
      <button id="cla" class="dentro" @click="cargar">Buscar</button><br><br>
      <div class="habi">
        <h3 id="n">#{{ idPok }}</h3>
        <h3 id="t">Nombre: {{ nombre }}</h3><br>
        <h4 id="t">Tipo: {{ tipopok }}</h4>


        <h4 id="t">Altura: {{ alturapok }} m</h4><br>
        <h4 id="t">Peso: {{ pesopok }} kg</h4><br>
        <div class="cota"></div>
      </div>
      <div class="pm">
      <img id="f" :src="imgPok" alt=""><br>
    </div>
      <table>
        <tbody>
          <tr>
            <div class="dis">
              <h2 id="e">Estadisticas</h2>
            </div>
            <div class="esta">
            <td>
            <th id="o">VIDA</th>
            <div class="stat-container">
              {{ vidapok }}
              <progress class="stat-bar1" max="255" :value="vidapok"></progress>
            </div>
            </td>
            <td>
            <th id="r">ATAQUE</th>
            <div class="stat-container">
              {{ ataquepok }}
              <progress class="stat-bar2" max="255" :value="ataquepok"></progress>
            </div>
            </td>
            <td>
            <th id="m">DEFENSA</th>
            <div class="stat-container">
              {{ defensapok }}
              <progress class="stat-bar3" max="255" :value="defensapok"></progress>
            </div>
            </td>
            <td>
            <th id="q">ATAQUE ESPECIAL</th>
            <div class="stat-container">
              {{ atakespok }}
              <progress class="stat-bar4" max="255" :value="atakespok"></progress>
            </div>
            </td>
            <td>
            <th id="x">DEFENSA ESPECIAL</th>
            <div class="stat-container">
              {{ defenespok }}
              <progress class="stat-bar5" max="255" :value="defenespok"></progress>
            </div>
            </td>
            <td>
            <th id="z">VELOCIDAD</th>
            <div class="stat-container">
              {{ velocidadpok }}
              <progress class="stat-bar6" max="255" :value="velocidadpok"></progress>
            </div>
            </td>
          </div>
          </tr>
        </tbody>
      </table>

    </div>
  </div>

</template>

<script setup>
import axios from "axios";
import { ref } from "vue";

let name = ref("");
let imgPok = ref("");
let idPok = ref("");
let alturapok = ref("");
let pesopok = ref("");
let tipopok = ref("");
let nombre = ref("");
let vidapok = ref("");
let ataquepok = ref("");
let defensapok = ref("");
let atakespok = ref("");
let defenespok = ref("");
let velocidadpok = ref("");

async function cargar() {
  let rep = await axios.get(`https://pokeapi.co/api/v2/pokemon/${name.value.toLowerCase()}`);
  tipopok.value = rep.data.types.map(typeInfo => typeInfo.type.name).join(", ");
  nombre.value = rep.data.name;
  imgPok.value = rep.data.sprites.other["official-artwork"].front_default;
  idPok.value = rep.data.id;
  alturapok.value = rep.data.height;
  pesopok.value = rep.data.weight;
  vidapok.value = rep.data.stats[0].base_stat;
  ataquepok.value = rep.data.stats[1].base_stat;
  defensapok.value = rep.data.stats[2].base_stat;
  atakespok.value = rep.data.stats[3].base_stat;
  defenespok.value = rep.data.stats[4].base_stat;
  velocidadpok.value = rep.data.stats[5].base_stat;
}

</script>

<style>
@font-face {
  font-family: "Noteworthy Light";
  src: url("https://db.onlinewebfonts.com/t/016f50054d487d421dc18257a191a3ad.eot");
  src: url("https://db.onlinewebfonts.com/t/016f50054d487d421dc18257a191a3ad.eot?#iefix")format("embedded-opentype"),
    url("https://db.onlinewebfonts.com/t/016f50054d487d421dc18257a191a3ad.woff2")format("woff2"),
    url("https://db.onlinewebfonts.com/t/016f50054d487d421dc18257a191a3ad.woff")format("woff"),
    url("https://db.onlinewebfonts.com/t/016f50054d487d421dc18257a191a3ad.ttf")format("truetype"),
    url("https://db.onlinewebfonts.com/t/016f50054d487d421dc18257a191a3ad.svg#Noteworthy Light")format("svg");
}

.contenedor{
  width: 90%; 
  margin: 0 auto; 
  padding: 20px; 
  box-sizing: border-box; 
}



.titulo {
  font-family: "Noteworthy Light";
  justify-content: center;
  text-align: center;
  background-image: url(./c814de67271c3abcbc2aef18035ca0dc-removebg-preview.png);
  background-size: contain;
  height: 300px;
  margin-top: -6%;
  font-size: 3em; /* Tamaño de fuente responsive */
  text-align: center;
  margin-bottom: 17px; /* Agrega espacio debajo del encabezado */

}

body {
  background-color: rgb(0, 0, 0);
}

#tlr {
  position: absolute;
  top: 15%;
  justify-content: center;
  text-align: center;
  left: 35%;
  color: #f3f3f3;

}

.caja {
  justify-content: center;
  text-align: center;
  border-radius: 35px 0px 35px 0px;
  -moz-border-radius: 35px 0px 35px 0px;
  -webkit-border-radius: 35px 0px 35px 0px;
  border: 2px solid #000000;
  height: 40px;
  margin-top: 2%;
  box-shadow:
    0 4px 18px rgba(255, 0, 0, 0.6),

    0 4px 8px rgba(0, 255, 0, 0.6),
  
    0 1px 3px rgba(255, 255, 0, 0.6),
   
    0 4px 8px rgba(0, 0, 255, 0.6);
  
  width: 100%; 
  max-width: 400px; 
  margin-bottom: 20px; 
  

}


@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}




.cota {
  position: absolute;
  top: 75%;
  left: 12%;
  width: 10vw; /* Cambiado a porcentaje del ancho de la ventana */
  height: 18vh; /* Cambiado a porcentaje del alto de la ventana */
  transform: rotate(50deg);
  border: 0.5vw solid #ffffff; /* Usar vw para hacer que las dimensiones del borde sean proporcionales */
  border-left: 0.5vw solid #ffffff;
  border-radius: 50%; /* Cambiado a porcentaje para asegurar que el borde sea redondo */
  border-right: 0.6vw solid #ffffff;
  animation: spin 4s reverse infinite linear;
}

.habi {
  display: flex;
  flex-direction: column;
  margin-left: -75%;
  gap: 0;
  color: white;
  font-family: "Noteworthy Light";

}


#f {
  position: absolute;
  justify-content: center;
  align-items: center;
  align-content: center; 
  width: 500px;
  height: auto;
  filter: drop-shadow(20px 7px 5px rgb(255, 255, 255));
  top: 29%;

}

.pm{
  right: 37%;
  position: absolute;
  justify-content: center;
  align-items: center;
  align-content: center;
  bottom: 40%;
}





.dentro {
  color: #000000;
  border: 2px solid #ffffff(0, 0, 0);
  border-radius: 0px;
  padding: 18px 36px;
  letter-spacing: 1px;
  cursor: pointer;
  box-shadow:
    0 4px 8px rgba(255, 0, 0, 0.6),
  
    0 4px 8px rgba(0, 255, 0, 0.6),

    0 0 5px rgba(255, 255, 0, 0.6),
  
    0 4px 8px rgba(0, 0, 255, 0.6);
 
  width: 100%; 
  max-width: 200px; 
  margin: 0 auto; 
  margin-bottom: 20px; 
  -webkit-transition: ease-out 0.4s;
  -moz-transition: ease-out 0.4s;
  transition: ease-out 0.4s;

}


.dentro:hover {
  box-shadow: inset 0 0 0 50px #aeb4d1;
}

#cla {
  height: 40px;
  margin: 50px auto 0 auto;
  text-align: center;
  position: absolute;
  border-radius: 0px 20px 0px 20px;
  left: 71%;
  top: 43.5%;
  font-family: "Noteworthy Light";
  font-size: 100%;

}


#fto {
  background-repeat: repeat;
}

.stat-column {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

}

/* .stat-bar {
  width: 50%;
  margin-top: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
} */

table {
  width: 100%;
  border-collapse: collapse;
 
  margin-bottom: 20px; 
}

th,
td {
  text-align: center;
  padding: 10px;
  display: flex;
  flex-direction: column;

}

th {

  display: flex;
  flex-direction: column;

}

td {
  background-color: rgb(0, 0, 0);
  vertical-align: middle;

}

.stat-container {
  font-family: "Noteworthy Light";
  margin: 20px;
  text-align: center;

}

#o {
  font-family: "Noteworthy Light";
  color: #ffffff;
  font-size: 160%;
  text-shadow: 2px 10px 10px rgba(16, 0, 242, 0.5);

}

#m {
  font-family: "Noteworthy Light";
  color: #ffffff;
  font-size: 160%;

  text-shadow: 2px 10px 10px rgba(8, 235, 0, 0.5);
}

#r {
  font-family: "Noteworthy Light";
  color: #ffffff;
  font-size: 160%;
  text-shadow: 2px 10px 10px rgba(255, 0, 0, 0.5);

}

#q {
  font-family: "Noteworthy Light";
  color: #ffffff;
  font-size: 160%;
  text-shadow: 2px 10px 10px rgba(0, 247, 255, 0.5);
}

#x {
  font-family: "Noteworthy Light";
  color: #ffffff;
  font-size: 160%;
  text-shadow: 2px 10px 10px rgb(255, 251, 0);
}

#z {
  font-family: "Noteworthy Light";
  color: #ffffff;
  font-size: 160%;
  text-shadow: 2px 10px 10px rgba(119, 14, 122, 0.5);

}

.stat-bar {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;

  max-width: 100%; 
}

.stat-bar1 {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;
}


.stat-bar::-webkit-progress-bar {
  background: transparent;
}

.stat-bar::-webkit-progress-value {
  background: linear-gradient(90deg, #58563f 0%, #58563f 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar::-moz-progress-bar {
  background: linear-gradient(90deg, #4caf50 0%, #81c784 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar1::-webkit-progress-bar {
  background: transparent;
}

.stat-bar1::-webkit-progress-value {
  background: linear-gradient(90deg, #4b83f3 0%,#4b83f3 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar1::-moz-progress-bar {
  background: linear-gradient(90deg, #355bf5 0%, #355bf5 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

#e {
  color: #e0e0e0;

  text-shadow: 2px 10px 10px rgb(106, 109, 106);

  font-family: "Noteworthy Light";

}


.stat-bar1:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

.stat-bar2 {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;
}


.stat-bar2::-webkit-progress-bar {
  background: transparent;
}

.stat-bar2::-webkit-progress-value {
  background: linear-gradient(90deg, #ad1d1d 0%, #ad1d1d 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar2::-moz-progress-bar {
  background: linear-gradient(90deg, #ad1d1d 0%, #ad1d1d 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar2:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

.stat-bar3 {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;
}


.stat-bar3::-webkit-progress-bar {
  background: transparent;
}

.stat-bar3::-webkit-progress-value {
  background: linear-gradient(90deg, #16662a 0%, 16662a 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar3::-moz-progress-bar {
  background: linear-gradient(90deg, #16662a 0%, #16662a 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar3:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

.stat-bar4 {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;
}


.stat-bar4::-webkit-progress-bar {
  background: transparent;
}

.stat-bar4::-webkit-progress-value {
  background: linear-gradient(90deg, #1a998e 0%, #1a998e 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar4::-moz-progress-bar {
  background: linear-gradient(90deg, #1a998e 0%, #1a998e 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar4:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

.stat-bar5 {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;
}


.stat-bar5::-webkit-progress-bar {
  background: transparent;
}

.stat-bar5::-webkit-progress-value {
  background: linear-gradient(90deg, yellow 0%, yellow 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar5::-moz-progress-bar {
  background: linear-gradient(90deg, yellow 0%, yellow 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar5:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

.stat-bar6 {
  width: 100%;
  height: 30px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  border-radius: 15px;
  overflow: hidden;
  background: linear-gradient(90deg, #f3f3f3 0%, #e0e0e0 100%);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2), inset 0 2px 5px rgba(255, 255, 255, 0.1);
  position: relative;
}


.stat-bar6::-webkit-progress-bar {
  background: transparent;
}

.stat-bar6::-webkit-progress-value {
  background: linear-gradient(90deg, #5c1456 0%, #5c1456 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar6::-moz-progress-bar {
  background: linear-gradient(90deg, #5c1456 0%, #5c1456 100%);
  transition: width 0.5s ease-in-out;
  border-radius: 15px;
}

.stat-bar6:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  pointer-events: none;
  animation: shimmer 1.5s infinite;
}

@keyframes shimmer {
  0% {
    background-position: -100% 0;
  }

  100% {
    background-position: 100% 0;
  }
}

.stat-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: Arial, sans-serif;
  margin: 20px;
  text-align: center;

}

.stat-container span {
  display: block;
  margin-bottom: 10px;
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

@media screen and (max-width: 1150px){

#tlr{
  justify-content: center;
  align-items: center;
  position: absolute;
  left: 40%;
  top: 60px;

 }
 #cla{
  margin-top: -10%;
  margin-left: -10%;
 }

 }
 /* .pm{
  position: absolute;
  top:22%;
  right: 38%;
 }

  */
 

@media screen and (max-width: 2042px) {
 
 #tlr{
  justify-content: center;
  align-items: center;
  position: absolute;
  left: 42%;
 }

 .caja{
  margin-top: 7%;
 }

 #cla{
  margin-top: -3%;
  margin-left: -10%;
 }
 .cota{
  margin-top:-px ;
  position: absolute;
 }

 #f{

  position: absolute;
  bottom: 3%;
  right: 38%;
 }
}

@media screen and (max-width: 1694px) {
#cla{
  margin-top: -62px;
  margin-left: 1px;
}
}

.cota{
  margin-top:-15% ;
 }

 #f{

position: absolute;
bottom: 3%;
right: 30%;
}



@media screen and (max-width: 1418px){
  .cota{
  margin-top:-19% ;
  /* width: 12%;
  height: 12%; */
 }

 #f{
  position: absolute;
bottom: 3%;
right: 15%;
 }
}

@media screen and (max-width: 1002px){
  #tlr{
  justify-content: center;
  align-items: center;
  position: absolute;
  left: 35%;
 }
 .cota{
  margin-top:-25% ;
  /* width: 12%;
  height: 12%; */
  margin-left: 33%;
 
 }
 .esta{
  margin-top: 90%;
 }

 .dis{
  margin-top: 60%;
  position: absolute;
  left: 35%;
 }

 .habi{
margin-left:2%;
 }

 #f{
  position: absolute;
  top: 105%;
  right: 25%;
 }

 #cla{
  margin-top: -8%;
  margin-left: 3%;
 }
 
}
@media screen and (max-width: 798px){
  #cla{
  margin-top: -17px;
  margin-left: -33%;
  }
  .cota{
    /* height: 13%;
    width: 16%; */
    top: 50%;
    left: 10%;
    width: 15vw;
    height: 25vh;
    border-width: 0.7vw;
    border-right-width: 0.8vw;
  }

  #f{position: absolute;
top: 110%;
right: 15%;
 }
  .habi{
    margin-top: 8%;
  }
  .contenedor {
    width: 80%;
    margin: 0 auto;
    padding: 15px;
  }
}

@media screen and (max-width: 655px){
  #tlr{
    margin-left: -7%;
  }

  #cla{
    margin-left: -35%;
  }

  .cota{
    margin-top: -27%;
  }

  #f{
    position: absolute;
    left: 18%;
    width: 450px;

  height: auto;
  }
  .dis{
    margin-left: -20px;
  }
}

@media screen and (max-width:569px){
  .esta{
margin-top: 110%;
  }
  .dis{
    margin-left: -30px;
    margin-top: 70%;
  }

}
@media (max-width: 480px) {
 .contenedor {
    width: 95%;
    margin: 0 auto;
    padding: 10px;
  }
}

</style>