<template>
    <div class="app font-monospace">
        <div class="content">
            <AppInfo :allMoviesCount="movies.length" :favoriteMoviesCount="movies.filter(c => c.favorite).length"/>
            <div class="search-panel">
                <SearchPanel :updateTermHandler="updateTermHandler"/>
                <AppFilter :updateFilterHandler="updateFilterHandler" :filterName="filter"/>
            </div>
            <MovieList :movies="onFilterHandler(onSearchHandler(movies, term), filter)" @onToggle="onToggleHandler" @onRemove="onRemoveHandler"/>
            <MovieAddForm @createMovie="createMovie"/>
        </div>
    </div>
</template>

<script>
import AppInfo from '@/components/app-info/AppInfo.vue';
import SearchPanel from '../search-panel/SearchPanel.vue';
import AppFilter from '../app-filter/AppFilter.vue'
import MovieList from '../movie-list/MovieList.vue'
import MovieAddForm from '../movie-add-form/MovieAddForm.vue'
export default { 
    components: {
    AppInfo,
    SearchPanel,
    MovieList,
    MovieAddForm,
    AppFilter,
} ,
data(){
      return{ 
        movies:[
          {
            id:1,
            name:'Capitan-America',
            viewers:344,
            favorite:false,
            like:false
          },
          {
            id:2,
            name:'Spider-man new home',
            viewers:744,
            favorite:false,
            like:false
          },
          {
            id:3,
            name:'Avengers-6:Kang dynasty',
            viewers:1544,
            favorite:false,
            like:false
          },
        ],
        filter: '',
        term: '',
      }
    },
    methods:{
        createMovie(item){
            this.movies.push(item)
        },
        onToggleHandler({id, prop}){
            this.movies = this.movies.map(item => {
                if(item.id == id){
                    return {...item, [prop]: !item[prop]}
                    // item. = !item.prop
                }
                return item
            })
        },
        onRemoveHandler(id){
            this.movies = this.movies.filter(c => c.id !== id)
            console.log(id);
        },
        onSearchHandler(arr, term){
            if(term.length == 0){
                return arr
            }
            return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
        },
        onFilterHandler(arr,filter){
            switch(filter){
                case 'popular': 
                    return arr.filter(c => c.like)
                case 'mostViewers':
                    return arr.filter(c => c.viewers > 500)    
                default: 
                    return arr    
            }
        },
        updateTermHandler(term){
            this.term = term
        },
        updateFilterHandler(filter){
            this.filter = filter
        }
    },
}

</script>
<style>
    .app{
        height: 100vh;
        color: black;
    }
    .content{
        width: 1000px;
        min-height: 700px;
        background-color: #fff;
        margin: 0 auto;
        padding: 5rem 0;
    }
    .search-panel{
        margin-top: 2rem;
        padding: 1.5rem;
        background-color: #f5f6fa;
        border-radius: 4px;
        box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
    }
</style>