<template>
<div>
<searchJokes v-on:search-text="searchText"/>
<joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke" />
</div>
</template>

<script>
import axios from 'axios';
import joke from '../../components/joke.vue'
import searchJokes from '../../components/searchJokes.vue'
export default {
    components:{
       joke ,
       searchJokes
    },
data(){
    return{
        jokes: []
    }
},
async created(){
    const config = {
        headers: {
            'Accept':'application/json'
        }
    }
    try {
    const res= await axios.get('https://icanhazdadjoke.com/search', config);
    this.jokes = res.data.results
    } catch (err) {
        console.log(err)
    }

},
methods:{
   async searchText(text ){
        const config = {
            headers: {
                'Accept':'application/json'
            }
        }
        try {
        const res= await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
        this.jokes = res.data.results
        } catch (err) {
            console.log(err)
        }
    }
},
head(){
    return{
        title:"Dad Jokes",
        meta: [
            {
                hid: "discription",
                name: "discription",
                content: "Best place for corny dad jokes"
            }
        ]
    }
}

}
</script>

<style>

</style>
