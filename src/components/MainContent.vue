<script>
import axios from 'axios';
import FilmItem from './FilmItem.vue';
import Header from './Header.vue';
export default{
    components:{
        FilmItem,
        Header,
    },
    data(){
        return{
            filmList : [],
            filmApiUrl : 'https://api.themoviedb.org/3/search/movie',
            filmApiKey : '0d49198008396e97d715e909d25476c0',
        }
    },
    methods:{
        getFilmList(searchQuery){
            axios.get( this.filmApiUrl, {
                params: {
                    api_key:this.filmApiKey,
                    query:searchQuery,
            },
            })
            .then(response =>{
                console.log(response.data.results);
                this.filmList= response.data.results;
            })
            .catch(function (error) {
                console.log(error);
            })
            .finally(function () {
                // always executed
            })  
        }
    },
    created(){
    }
}

</script>

<template>
    <div>
        <Header @search="getFilmList" />
        <main>
            <div v-if="filmList.length">
                <h3>
                    Search Results:
                </h3>
                <div class="film-list">
                    <FilmItem v-for="film in filmList" :key="film.id" :film="film" />
                </div>
            </div>
        </main>
    </div>

</template>

<style lang="scss">

@use '../styles/partials/flagIcons' as *;

</style>