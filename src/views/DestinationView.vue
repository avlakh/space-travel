<template>
    <main class="grid-container grid-container--destination">
        <h1 class="numbered-title"><span aria-hidden="true">01</span>Pick your destination</h1>
        <img v-if="this.planet === 'Moon'" src="../assets/images/destination/image-moon.png" alt="The Moon"/>
        <img v-if="this.planet === 'Mars'" src="../assets/images/destination/image-mars.png" alt="Mars"/>
        <img v-if="this.planet === 'Europa'" src="../assets/images/destination/image-europa.png" alt="Europa"/>
        <img v-if="this.planet === 'Titan'" src="../assets/images/destination/image-titan.png" alt="The Moon"/>

        <div class="tab-list underline-indicators flex">
            <button 
                :aria-selected="true ? this.planet == 'Moon' : false" 
                class="uppercase ff-sans-cond text-accent bg-dark letter-spacing-2" 
                @click="this.planet = 'Moon'">Moon</button>
            <button 
                :aria-selected="true ? this.planet == 'Mars' : false" 
                class="uppercase ff-sans-cond text-accent bg-dark letter-spacing-2" 
                @click="this.planet = 'Mars'">Mars</button>
            <button 
                :aria-selected="true ? this.planet == 'Europa' : false" 
                class="uppercase ff-sans-cond text-accent bg-dark letter-spacing-2" 
                @click="this.planet = 'Europa'">Europa</button>
            <button 
                :aria-selected="true ? this.planet == 'Titan' : false" 
                class="uppercase ff-sans-cond text-accent bg-dark letter-spacing-2" 
                @click="this.planet = 'Titan'">Titan</button>
        </div>
        <template v-if="this.planet === 'Moon'" v-for="(item, i) in planetsArr.destinations">
            <DestinationPlanet 
                :key="i" 
                v-if="(i === 0)"
                :name="item.name"
                :description="item.description"
                :distance="item.distance"
                :travel="item.travel"/>
        </template>
        <template v-if="this.planet === 'Mars'" v-for="(item, i) in planetsArr.destinations">
            <DestinationPlanet 
                :key="i" 
                v-if="(i === 1)"
                :name="item.name"
                :description="item.description"
                :distance="item.distance"
                :travel="item.travel"/>
        </template>
        <template v-if="this.planet === 'Europa'" v-for="(item, i) in planetsArr.destinations">
            <DestinationPlanet 
                :key="i" 
                v-if="(i === 2)"
                :name="item.name"
                :description="item.description"
                :distance="item.distance"
                :travel="item.travel"/>
        </template>
        <template v-if="this.planet === 'Titan'" v-for="(item, i) in planetsArr.destinations">
            <DestinationPlanet 
                :key="i" 
                v-if="(i === 3)"
                :name="item.name"
                :description="item.description"
                :distance="item.distance"
                :travel="item.travel"/>
        </template>

    </main>
</template>

<script>
import axios from 'axios';
import DestinationPlanet from '../components/DestinationPlanet.vue';

export default {
    components: { 
        DestinationPlanet 
    },
    data() {
        return {
            planet: 'Moon',
            planetsArr: []
        }
    },
    created(){
        axios
            .get('data.json')
            .then(resp => {
                this.planetsArr = resp.data;
            })
    }
}

</script>

<style lang="scss" scoped>
.grid-container--destination {
    grid-template-areas: 
    'title'
    'image'
    'tabs'
    'content';
}

.grid-container--destination {
    .numbered-title {
        grid-area: title;
    }
    img {
        grid-area: image;
        max-width: 60%;
    }
    .tab-list {
        grid-area: tabs;
    }
}


.tab-list {
    flex-wrap: wrap;
    justify-content: center;
}

@media (min-width: 50em){
    .numbered-title {
        justify-self: start;
        margin-top: 2rem;
    }
    .grid-container--destination {
        justify-items: start;
        grid-template-areas: 
            '. title title .'
            '. image tabs .'
            '. image content .';
    }
    .grid-container--destination img {
        max-width: 90%;
    }
}

</style>