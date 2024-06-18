<script>
export default{
    name: 'Header',
    data(){
        return{
            searchQuery: '',
        }
    },
    methods:{
        search(){
            this.$emit('search',this.searchQuery);
        }
    }
}

</script>
<template>
    <header>
        <div class="logo">
            BOOLFLIX
        </div>
        <input v-model="searchQuery" @keyup.enter="search" placeholder="Search for movies or TV shows" >
    </header>
</template>
<style scoped>

</style>