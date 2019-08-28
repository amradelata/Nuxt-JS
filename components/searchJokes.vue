<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="text" placeholder="Search Jokes...">
        <input type="submit" value="search jokes">
    </form>
</template>

<script>
export default {
    name: 'SearchJokes',
    data(){
        return {
            text: ''
        }
    },
    methods:{
      onSubmit(){
          this.$emit('search-text', this.text)
          this.text="";
      }  
    }
}
</script>

<style scoped>
input[type=text]{
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    width: 80%;
}
input[type=submit]{
    width: 15%;
    padding: 10px;
    border-radius: 5px;
    background: #00a8ff;
    color:#fff;
    border: none
}

</style>
