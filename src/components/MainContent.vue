<script>
import axios from 'axios';
export default{
    components:{

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

    <div>
        <h3>
            Search Results:
        </h3>
        <ul>
            <li v-for="film in filmList" :key="film.id">
                <p>
                    Titolo: {{ film.title }}
                </p>
                <p>
                    Titolo Originale: {{ film.original_title }}
                </p>
                <p>
                    Lingua: {{ film.original_language }}
                </p>
                <p>
                    Voto: {{ film.vote_average }}
                </p>
            </li>
        </ul>
    </div>
</main>

</template>

<style>

</style>