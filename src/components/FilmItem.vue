<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faStar as fasStar } from '@fortawesome/free-solid-svg-icons';
import { faStar as farStar } from '@fortawesome/free-regular-svg-icons';
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
    components:{
        FontAwesomeIcon,
    }
}

</script>

<template>
<div class="film-item">
    <img :src="getImageUrl(film.poster_path)" :alt="film.title">
    <div class="film-info">
        <p><strong>Titolo:</strong> {{ film.title }}</p>
        <p><strong>Titolo Originale:</strong> {{ film.original_title }}</p>
        <p><strong>Lingua:</strong><span class="lang-icon" :class="'lang-icon-' + film.original_language"></span></p>
        <p><strong>Voto:</strong> 
            <span v-for="n in 5" :key="n" class="star">
                <font-awesome-icon :icon="n <= starRating ? 'fas fa-star' : 'far fa-star'" />
            </span>
        </p>
            <p><strong>Overview:</strong> {{ film.overview }}</p>
    </div>
</div>
</template>

<style lang="scss">

@use '../styles/partials/_filmItem';

</style>