 <template>
 <div v-for="post in posts.results" :key="post" >
        <div>
            <img :src="getUrl(post.backdrop_path)">
        </div>

        <h2>Titre : </h2>
        <h3>{{post.original_title}}</h3>
        <div class ="plusdetails">
            <h5>Date de sortie: {{post.release_date}}</h5>
            <h5>Note : {{post.vote_average}} / 10</h5>
            <h5>Nombre de votes : {{post.vote_count}}</h5>
        </div>
        <h2>Description : </h2>
        <p>{{post.overview}}</p>
    </div>

</template>

<script>
export default {
    name: "PageFilms",
     methods: {
        async getData() {
            try {
                let response = await fetch('https://api.themoviedb.org/3/movie/popular?api_key=fd86e8643ea7662a2db2ac136460593d&language=fr-fr');
                this.posts = await response.json();
            } catch (error) {
                console.log(error);
            }
        },
        getUrl(pathImg) {
            return this.LinkImg + pathImg;
        }
    },
    data() {
        return {
            posts: [],
            LinkImg: "https://image.tmdb.org/t/p/original",
        }
    },
    mounted() {
        this.getData();
    }
}
</script>

<style scoped>
img{
    height: auto;
    width: 800px;
    max-width: 100%;
    margin-top: 60px;

}
h2{
    color: white;
    font-size: 30px;
}
h3{
    color: red;
    font-size: 30px;
}
p{
    color: grey;
    margin: 0 auto;
    width: 800px;   
    max-width: 100%;
    font-size: 20px;
    margin-bottom: 100px;
}
.plusdetails{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.plusdetails * {
    margin: 0 10px;
}
</style>