<template>
    <ul class="movie-list list-group">
      <MovieListItem 
      v-for="movie in movies" 
      :movie="movie" 
      :key="movie.id" 
      @onToggle="$emit('onToggle', $event)"
      @onRemove="$emit('onRemove', movie.id)"
      />
    </ul>
</template>
<script>
import MovieListItem from '../movie-list-item/MovieListItem.vue';
export default {
    components: { MovieListItem }, 
    props:{
      movies:{
        type:Array,
        required:true,
      }
    }
}
</script>
<style>
    .movie-list{
      margin-bottom: 2rem;
      margin-top: 2rem;
      padding: 1.5rem;
      background-color: #f5f6fa;
      border-radius: 4px;
      box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
    }
</style>