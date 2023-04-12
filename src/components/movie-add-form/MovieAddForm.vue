<template>
    <div class="movie-add-form">
        <h3>Add new movie</h3>
        <form class="add-form d-flex" @submit.prevent>
            <input type="text"
             class="form-control new-movie-label" 
             placeholder="What kind of movie?" 
             @input="name = $event.target.value" 
             :value="name">
            <input type="number" 
            class="form-control new-movie-label" 
            placeholder="Seen how many times" 
            @input="viewers = $event.target.value"
            :value="viewers">
            <button class="btn btn-outline-dark" @click="addMovie" type="submit">Add</button>
        </form>
    </div>
</template>
<script>
export default {
    data(){
        return{
            name:'',
            viewers:'',
        }
    },
    methods:{
        addMovie(){
            if(!this.name || !this.viewers) return
            const newMovie = {
                name:this.name,
                viewers:this.viewers,
                favorite:false,
                like:false,
                id:Date.now
            }
            this.$emit('createMovie', newMovie)
            this.name =''
            this.viewers = ''
        }
    },
}
</script>
<style>
    .movie-add-form{
        margin-top: 2rem;
        padding: 1.5rem;
        background-color: #f5f6fa;
        border-radius: 4px;
        box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
    }
</style>