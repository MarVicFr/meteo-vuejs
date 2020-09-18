<template>
  <div class="container">
    <h1 class="my-4">App Meteo Vue JS</h1>
    <div class="form-group mb-5">
      <label for="position">Entrer le nom de la ville :</label>
      <input
        id="position"
        type="text"
        class="form-control"
        v-model="requete"
        @keypress="goMeteo"
      />
    </div>
    <div class="w-75 m-auto" v-if="temps">
      <h3 class="text-center">Position: {{ temps.name }}</h3>
      <div class="card text-center p-5">
        <p class="text-affichage">Temperature : {{ temps.main.temp.toFixed() }} °c</p>
        <p class="text-affichage">Temps : {{ temps.weather[0].description }}</p>
      </div>
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  name: "Meteo",
  data() {
    return {
      requete: "",
      temps: undefined,
      api_code: "6d86330052fd188f9affbca8cc8dd6cb",
      url_recherche: "https://api.openweathermap.org/data/2.5/weather?"
    };
  },
  methods: {
    goMeteo(event) {
      if (event.key == "Enter") {
        axios
          .get(
            `${this.url_recherche}q=${this.requete}&units=metric&APPID=${this.api_code}&lang=fr`
          )
          .then(reponse => {
            // console.log(reponse)
            this.temps = reponse.data;
          });
        this.requete = "";
      }
    }
  }
};
</script>



<style>
.text-affichage {
  font-size: 30px;
  font-weight: 300;
  line-height: 1.2;
}
</style>