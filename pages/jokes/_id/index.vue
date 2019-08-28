<template>
    <div>
        <!-- {{$route.params.id}}  -->
        <!-- to get parames -->
        <nuxt-link to="/jokes">Back to jokes</nuxt-link>
        <h2>{{joke}}</h2>
        <hr />
        <small>joke ID: {{$route.params.id}}</small>
    </div>
</template>

<script>
import axios from 'axios'
export default {
data(){
    return{
        joke: {
             
        }
    }
},
async created(){
    const config = {
        headers: {
            'Accept':'application/json'
        }
    }
    try {
    const res= await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
    this.joke = res.data.joke
    } catch (err) {
        console.log(err)
    }
},
head(){
    return{
        title: this.joke,
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
