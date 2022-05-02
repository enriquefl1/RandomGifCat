<template>
  <div id="app">
    <div class="container border">
      <div class="row">
        <div class="col-12 sectionTitle">
          <h1>Random Gif Cat</h1>
        </div>
        <section class="formulario">
          <div class="col-12 sectionTitulo">
            <label>Titulo :</label>
            <input v-model="valorTitulo" placeholder="escriba un titulo" />
          </div>
          <div class="col-12 sectionFiltro">
            <label>Filtro :</label>
            <select v-model="valorFiltro" id="valorFiltro">
              <option value="blur">blur</option>
              <option value="mono">mono</option>
              <option value="sepia">sepia</option>
              <option value="negative">negative</option>
              <option value="paint">paint</option>
              <option value="pixel">pixel</option>
            </select>
          </div>
          <div class="col-12 sectionColor">
            <label>Color :</label>
            <select v-model="valorColor" id="valorCalor">
              <option value="yellow">amarillo</option>
              <option value="blue">azul</option>
              <option value="orange">naranjo</option>
              <option value="red">rojo</option>
            </select>
            <div class="circle" :style="`backgroundColor: ${valorColor}`"></div>
          </div>
          <div class="col-12 sectionTamano">
            <label>Tamaño :</label>
            <input
              type="number"
              min="30"
              max="500"
              v-model="valorTamano"
              placeholder="De 30 a 500 px"
            />
          </div>
          <div class="col-12">
            <input
              type="button"
              value="Obtener mi gatito"
              @click="clickBoton"
            />
          </div>
        </section>
        <section class="sectionImagen">
          <div class="col-12">
            <img :src="imagenGato" alt="" />
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      valorTitulo: "",
      valorFiltro: "blur",
      valorColor: "orange",
      valorTamano: "",
      imagenGato: "",
    };
  },
  methods: {
    getData() {
      this.imagenGato = `https://cataas.com/cat/gif/says/${this.valorTitulo}?filter=${this.valorFiltro}&color=${this.valorColor}&size=${this.valorTamano}&type=or`;
    },
    clickBoton() {
      if (this.valorTitulo === "" || this.valorTamano === "") {
        alert("Debe escribir un valor para Titulo y Tamaño");
      } else {
        this.getData();
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 1px;
}

* {
  padding: 0;
  margin: 0;
}

.sectionTitle {
  background-color: cadetblue;
}

.formulario {
  background-color: tomato;
}
.sectionImagen {
  background-color: cadetblue;
}

.circle {
  background-color: tomato;
  width: 20px;
  height: 20px;
  border-radius: 50%;
}

.sectionColor,
.sectionTitulo,
.sectionFiltro,
.sectionTamano {
  display: flex;
  justify-content: left;
  margin-left: 180px;
}
</style>
