<template>
    <div class="app-info">
        <p class="fs-3 text-uppercase">Number of all movies: {{ allMoviesCount }}</p>
        <p class="fs-4 text-uppercase">Number of movies watched: {{ favoriteMoviesCount }}</p>
    </div>
</template>

<script>
import { number } from 'prop-types';

export default {
    props:{
        allMoviesCount:{
            type:Number,
            required:true
        },
        favoriteMoviesCount:{
            type:Number,
            required:true
        }
    }
}
</script>
<style>
.app-info{
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #f5f6fa;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>