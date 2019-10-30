<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <b-container fluid>
      <b-row class="justify-content-md-center pt-5">
        <b-col col sm="3">
          <b-form-select v-if="!resultone.length" v-model="selectedone" :options="options"></b-form-select>
        </b-col>

        <b-col col sm="3">
          <b-form-select v-if="!resultone.length" v-model="selectedtwo" :options="options"></b-form-select>
        </b-col>
      </b-row>

      <b-row class="justify-content-md-center pt-5">
        <b-col col sm="6">
          <b-button
            variant="outline-primary"
            @click="compatibilizarone"
            v-if="!resultone.length"
          >Compatibilizar</b-button>
          <p class="pt-3" v-if="resultone.length">
            Ha quedado registrada la compatibilidad entre
            <strong>{{ selectedone }}</strong> y
            <strong>{{ selectedtwo }}</strong>
          </p>
        </b-col>
      </b-row>
      <!--Segunda fila-->
      <div v-if="resultone.length">
        <b-row class="justify-content-md-center pt-5">
          <b-col col sm="3">
            <b-form-select v-if="!resulttwo.length" v-model="selectedthree" :options="optionstwo"></b-form-select>
          </b-col>

          <b-col col sm="3">
            <b-form-select v-if="!resulttwo.length" v-model="selectedfour" :options="optionstwo"></b-form-select>
          </b-col>
        </b-row>

        <b-row class="justify-content-md-center pt-5">
          <b-col col sm="6">
            <b-button
              variant="outline-primary"
              @click="compatibilizartwo"
              v-if="!resulttwo.length"
            >Compatibilizar</b-button>
            <p class="pt-3" v-if="resulttwo.length">
              Ha quedado registrada la compatibilidad entre
              <strong>{{ selectedthree }}</strong> y
              <strong>{{ selectedfour }}</strong>
            </p>
          </b-col>
        </b-row>
      </div>
      <!--Tercera fila-->
      <div v-if="resulttwo.length">
        <b-row class="justify-content-md-center pt-5">
          <b-col col sm="3">
            <b-form-select
              v-if="!resultthree.length"
              v-model="selectedfive"
              :options="optionsthree"
            ></b-form-select>
          </b-col>

          <b-col col sm="3">
            <b-form-select v-if="!resultthree.length" v-model="selectedsix" :options="optionsthree"></b-form-select>
          </b-col>
        </b-row>

        <b-row class="justify-content-md-center pt-5 pb-5">
          <b-col col sm="6">
            <b-button
              variant="outline-primary"
              @click="compatibilizarthree"
              v-if="!resultthree.length"
            >Compatibilizar</b-button>
            <p class="pt-3" v-if="resultthree.length">
              Ha quedado registrada la compatibilidad entre
              <strong>{{ selectedfive }}</strong> y
              <strong>{{ selectedsix }}</strong>
            </p>
          </b-col>
        </b-row>
      </div>
      <div class="pt-5"></div>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "Compatibilidad",
  props: {
    msg: String
  },
  data() {
    return {
      remove: "",

      options: ["a", "b", "c", "d"],
      resultone: [],
      selectedone: null,
      selectedtwo: null,

      optionstwo: ["a", "b", "c", "d"],
      resulttwo: [],
      selectedthree: null,
      selectedfour: null,

      optionsthree: ["a", "b", "c", "d"],
      resultthree: [],
      selectedfive: null,
      selectedsix: null
    };
  },
  methods: {
    compatibilizarone() {
      if (this.selectedone !== this.selectedtwo) {
        this.resultone.push({
          slotone: this.selectedone,
          slottwo: this.selectedtwo
        });
        this.borrar();
      } else {
        this.alerta();
      }
    },
    compatibilizartwo() {
      if (this.selectedthree !== this.selectedfour) {
        this.resulttwo.push({
          slotone: this.selectedthree,
          slottwo: this.selectedfour
        });
        this.borrar();
      } else {
        this.alerta();
      }
    },
    compatibilizarthree() {
      if (this.selectedfive !== this.selectedsix) {
        this.resultthree.push({
          slotone: this.selectedfive,
          slottwo: this.selectedsix
        });
        this.borrar();
      } else {
        this.alerta();
      }
    },
    borrar() {
      this.remove = this.options.indexOf(this.selectedone);

      this.optionstwo.splice(this.remove, 1);
      this.optionsthree.splice(this.remove, 1);
    },
    alerta() {
      alert("No se pueden compatibilizar parámetros idénticos");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
