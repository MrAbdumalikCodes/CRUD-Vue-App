<template>
    <div class="btn-group">
        <button class="btn" @click="filterHandler('all')" :class="[filterName == 'all' ? 'btn-dark' : 'btn btn-outline-dark']" type="button">All movies</button>
        <button class="btn" :class="[filterName == 'popular' ? 'btn-dark' : 'btn btn-outline-dark']" @click="filterHandler('popular')" type="button">Popular movies</button>
        <button class="btn" :class="[filterName == 'mostViewers' ? 'btn-dark' : 'btn btn-outline-dark']" @click="filterHandler('mostViewers')" type="button">Most viewed movies</button>
    </div>
</template>
<script>
export default {
    props:{
        updateFilterHandler:{
            type:Function,
            required:true
        },
        filterName:{
            type:String,
            required:true
        }
    },
    data(){
        return {
            filter:'all'
        }
    },
    methods:{
        filterHandler(filter){
            this.filter = filter
            this.updateFilterHandler(this.filter)
        }
    }
}
</script>
<style>
    
</style>