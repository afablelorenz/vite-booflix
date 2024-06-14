<script>
import axios from 'axios';
export default{
    components:{

    },
    data(){
        return{
            filmList : [],
            filmApiUrl : 'https://api.themoviedb.org/3/search/movie',
            filmListSearch : 'star',
            filmApiKey : '0d49198008396e97d715e909d25476c0',
        }
    },
    methods:{
        getFilmList(){
            axios.get( this.filmApiUrl, {
                params: {
                    api_key:this.filmApiKey,
                    query:this.filmListSearch,
                    page:1
            },
            })
            .then(function (response) {
                console.log('entrato');
                console.log(response);
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
        this.getFilmList();
    }
}

</script>

<template>
<main>
    <input>
    <button>

    </button>
</main>

</template>

<style>

</style>