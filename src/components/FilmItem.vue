<script>
    export default{
        props:{
            film: Object,
        },
    methods: {
        getImageUrl(path){
            const baseUrl = 'https://image.tmdb.org/t/p/';
            const size = 'w342';
            return `${baseUrl}${size}${path}`;
        }
    },
    computed: {
        starRating(){
            
        }
    },
}

</script>

<template>
<div>
    <p>
        <img :src="getImageUrl(film.poster_path)" :alt="film.title" />
    </p>
    <p>
        Titolo: {{ film.title }}
    </p>
    <p>
        Titolo Originale: {{ film.original_title }}
    </p>
    <p>
        Lingua: <span class="lang-icon" :class="'lang-icon-' + film.original_language"></span>
    </p>
</div>
</template>

<style>

</style>