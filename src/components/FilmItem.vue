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
        starRating() {
            return Math.ceil(this.film.vote_average / 2);
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
    <p>
        Voto: 
        <span v-for="n in 5" :key="n" class="star">
            <font-awesome-icon :icon="n <= starRating ? 'fas fa-star' : 'far fa-star'" />
        </span>
    </p>
</div>
</template>

<style>
.star {
    color: gold;
}
</style>