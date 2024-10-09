<template>
  <div>
    <table>
      <ul>
        <button @click="obtenerPoblacion()">Obtener Población de Países</button>
        <li v-for="item in poblacion" :key="item.country">{{ item.country }}: {{ item.populationCounts[0].value }}</li>
      </ul>
      <ul>
        <button @click="obtenerRandomAnime()">Obtener anime random</button>
        <!--v-for="item in randomAnime" :key=""-->
        <!-- No alcanceeeeee :,) -->
      </ul>
      <ul>
        <button @click="obtenerRandomManga()">Obtener manga random</button>
      </ul>
      <ul>
        <button @click="obtenerRecomendaciones()">Obtener recomendaciones Anime</button>
      </ul>
    </table>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      poblacion: [],
      randomAnime: [],
      randomManga: [],
      recomendacionesAnime: []
    };
  },
  methods: {
    obtenerPoblacion() {
      fetch('https://countriesnow.space/api/v0.1/countries/population')
        .then(response => {
          return response.json();
        })
        .then(data => {
          this.poblacion = data.data;
          console.log(this.poblacion)
        })
        .catch(error => {
          console.error('Error al obtener los datos:', error);
        });
    },
    obtenerRandomAnime(){
      fetch('https://api.jikan.moe/v4/random/anime')
        .then(response => {
          return response.json();
        })
        .then(data => {
          this.randomAnime = data.data;
          console.log(this.randomAnime)
        })
        .catch(error => {
          console.error('Error al obtener los datos:', error);
        });
    },
    obtenerRandomManga(){
      fetch('https://api.jikan.moe/v4/random/manga')
        .then(response => {
          return response.json();
        })
        .then(data => {
          this.randomManga = data.data;
          console.log(this.randomManga)
        })
        .catch(error => {
          console.error('Error al obtener los datos:', error);
        });
    },
    obtenerRecomendaciones(){
      fetch('https://api.jikan.moe/v4/recommendations/anime')
        .then(response => {
          return response.json();
        })
        .then(data => {
          this.recomendacionesAnime = data.data;
          console.log(this.recomendacionesAnime)
        })
        .catch(error => {
          console.error('Error al obtener los datos:', error);
        });
    }
  }
}
</script>

<style>
</style>
