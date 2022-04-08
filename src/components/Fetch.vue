<template>
    <button @click="getDrink" :id="'get-beers'">Click me to see Beers!</button>
    <ul v-if="test">
        <li v-for="child in test" v-bind:key="child.name" :class="'total-beers'">
        <BeerList :name="child.name" :tagLine="child.tagline" :description="child.description" :imageUrl="child.image_url" :brewerTips="child.brewers_tips" :ingredients="child.ingredients" :contributedBy="child.contributed_by"/>
        </li>
    </ul>
</template>
<script>
import BeerList from './BeerList.vue';
export default {
    name:"FetchData",
    methods:{
        getDrink(){
        // Bring the data from the API.
        fetch('https://api.punkapi.com/v2/beers').then(res => res.json())
        .then(response =>{
        this.test = response;
    })
        }
    },
    components:{
        BeerList
    },
    data: ()=>({
        test: null
    })
}
</script>