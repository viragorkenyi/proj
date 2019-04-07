<template>

  <div id="app">
 <h1>Pizza rendelés</h1>
    <br>
    <div id="input">
    <input v-model="Nev" id ='inp'><br>
    <input v-model="Cim" id ='inp2'><br>
    <input v-model="Telefonszam" id ='inp3'><br>
    <br>
    </div>
    <div id='selec1'>
    <span>Válassz fajtát!</span><br>
    <select v-model="Fajta" class='sel'>
    <option disabled value="">Válassz fajtát!</option>
    <option>Margarita</option>
    <option>Songoku</option>
    <option>Magyaros</option>
    <option>Négysajtos</option>
    <option>Pepperonis</option>
    <option>Kukoricás</option>
    </select>
  </div>
    <div id=selec2>
    <br>
    <span>Válassz méretet!</span><br>
    <select v-model="Meret">
    <option disabled value="">Válassz méretet!</option>
    <option>18 cm</option>
    <option>28 cm</option>
    <option>32 cm</option>
    <option>45 cm</option>
    </select>
    <br>
      </div>
    <div id ='megj'>
    <span>Megjegyzés:</span>
    <p style="white-space: pre-line;">{{ message }}</p>
    <textarea v-model="Megjegyzes" placeholder="Megjegyzés"></textarea>
    <br>
    </div>
    <button @click="f()">Rendelés</button>
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      Nev: 'Név',
      Cim:'Cím',
      Telefonszam:'Telefonszám',
      Meret:'Méret',
      Fajta:'Fajta'
    }
  },
  methods: {
    f() {
    location.href = 'http://localhost:8081'
    this.axios.post('http://localhost:3000', {
    Nev: this.Nev,
    Cim: this.Cim,
    Telefonszam:this.Telefonszam,
    Fajta: this.Fajta,
    Meret:this.Meret,
    Megjegyzes:this.Megjegyzes,

  })
  .then(console.log)
    }
  }
}

</script>

<style>
#app {
  font-family: "Times New Roman", Times, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  background-color: #8a8a5c;
  border-radius: 8px;
  font-size:20px;
  padding:200px

}
#input{
background-color:#b8b894;
font-size:20px;
padding:10px;
  text-align: center;
color: #000000;
border-radius: 8px;
margin:20px;
box-shadow:10px 10px 5px black;
}
#selec1{
background-color: #5c5c3d;
font-size:20px;
  text-align: center;
padding:10px;
color: #000000;
border-radius: 8px;
margin:20px;
box-shadow:10px 10px 5px black;

}
#selec2{
background-color:#b8b894;
font-size:20px;
  text-align: center;
color: #000000;
border-radius: 8px;
padding:10px;
margin:20px;
box-shadow:10px 10px 5px ;

}
#megj{
background-color: #5c5c3d;
font-size:20px;
text-align: center;
color: #000000;
padding:10px;
border-radius: 8px;
margin:20px;
box-shadow:10px 10px 5px black;

}
#inp{
padding:5px;
margin:5px;
}
#inp2{
padding:5px;
margin:5px;
}
#inp3{
padding:5px;
margin:5px;
}
</style>
