<template>
    <h3 class="beer-tagline">{{tagLine}}</h3>
    <h1 class="beer-name">{{name}}</h1>
    <img :src="imageUrl" alt="Beer Image">
    <p class="beer-description"> You wonder what this taste is, eh buddy? It is {{description}}</p>
    <div class="beer-ingredients">
         You can search the names below to dig into them.
        <div v-for="malt in ingredients" :key="malt" :class="'beer-ingredients-2'">
            <li v-for="tips in malt" :key="tips" v-show="typeof tips === 'object'">
                -{{tips.name}}
                <!-- These loop do not recognize the tips.amount as an object
                even though (typeof tips.amount) returns object. 
                I think it has something to do with VueJS concepts.
                Left to solve later.
                 -->
            </li> 
        </div>
    </div>
    <p class="beer-tips">How to make it even better ? Listen, {{brewerTips}}</p>
    <h5 class="beer-contribute">Contributed by <span :class="'contributors'">{{contributedBy}}</span></h5>
</template>
<script>
export default {
    name: "BeersList",
    props:{
        tagLine: String,
        id: Number,
        description: String,
        name: String,
        imageUrl: String,
        ingredients: Object,
        brewerTips: String,
        contributedBy: String
    }
}
</script>