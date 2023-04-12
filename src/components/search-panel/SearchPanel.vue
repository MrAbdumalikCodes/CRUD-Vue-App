<template>
    <div>
        <input 
        type="text" 
        class="form-control search-input" 
        placeholder="Search movies..." 
        :value="term"
        @input="changeHandler">
    </div>
</template>
<script>
export default {
    props:{
        updateTermHandler:{
            type:Function,
            required:true
        }
    },
    data(){
        return{
            term:''
        }
    },
    methods:{
        changeHandler(e){
            this.term = e.target.value
            // console.log(e.target.value);
            this.updateTermHandler(this.term)
        }
    }
}
</script>
<style scoped>
    .search-input{
        margin-bottom: 2rem;
        margin-top: 2rem;
        padding: 1.5rem;
        background-color: #f5f6fa;
        border-radius: 4px;
        box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
    }
</style>