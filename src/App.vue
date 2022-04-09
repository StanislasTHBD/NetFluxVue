<template>
  <NavBar/>
  <PageFilms/>
</template>

<script>
import NavBar from './components/NavBar.vue'
import PageFilms from './components/PageFilms.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    PageFilms
  },
  methods:{
    async getData(){
      try {
        let response = await fetch("https://api.themoviedb.org/3/movie/popular?api_key=fd86e8643ea7662a2db2ac136460593dz");
        this.posts = await response.json();
        while(this.it < 20){
          this.title[this.it] = this.posts.results[this.it].title;
          this.backdrop_path[this.it] = this.posts.results[this.it].backdrop_path;
          this.overview[this.it] = this.posts.results[this.it].overview;
          this.release_date[this.it] = this.posts.results[this.it].release_date;
          this.vote_average[this.it] = this.posts.results[this.it].vote_average;
          this.vote_count[this.it] = this.posts.results[this.it].vote_count;
          this.it++
        }
      } catch (error) {
        console.log(error);
      }
    }
  },
  data() {
    return {
      title: [''],
      backdrop_path: [''],
      overview: [''],
      release_date: [''],
      vote_average: [''],
      vote_count: [''],
      posts: [],
      it: 0,
    }
  },
  created() {
    this.getData();
  }
} 
</script>

<style>
* {
  background: black;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
