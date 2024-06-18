<script>
import axios from 'axios';
import FilmItem from './FilmItem.vue';
export default{
    components:{
        FilmItem,
    },
    data(){
        return{
            filmList : [],
            filmApiUrl : 'https://api.themoviedb.org/3/search/movie',
            filmListSearch : '',
            filmApiKey : '0d49198008396e97d715e909d25476c0',
        }
    },
    methods:{
        getFilmList(){
            axios.get( this.filmApiUrl, {
                params: {
                    api_key:this.filmApiKey,
                    query:this.filmListSearch,
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
<main>
    <input v-model="filmListSearch" placeholder="Search a film">
    <button @click="getFilmList">
        Search
    </button>

    <div v-if="filmList.length">
        <h3>
            Search Results:
        </h3>
        <ul>
            <li v-for="film in filmList" :key="film.id">
                <FilmItem :film="film" />
            </li>
        </ul>
    </div>
</main>

</template>

<style lang="scss">

@use '../styles/partials/flagIcons' as *;

</style>