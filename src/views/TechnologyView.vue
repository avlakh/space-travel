<template>
    <main class="grid-container grid-container--technology">
        <h1 class="numbered-title"><span aria-hidden="true">03</span>Space launch 101</h1>
        <div class="numbered-indicators flex">
            <button 
                :aria-selected="true ? this.technologyName == 'vehicle' : false" 
                class="ff-serif fs-600"
                @click="this.technologyName = 'vehicle'"
                >1</button>
            <button 
                :aria-selected="true ? this.technologyName == 'port' : false" 
                class="ff-serif fs-600"
                @click="this.technologyName = 'port'"
                >2</button>
            <button 
                :aria-selected="true ? this.technologyName == 'capsule' : false" 
                class="ff-serif fs-600"
                @click="this.technologyName = 'capsule'"
                >3</button>
        </div>
        <template v-if="this.technologyName === 'vehicle'" v-for="(item, i) in technologyArr.technology">
            <TechnologyLaunch 
            :key="i"
            v-if="(i === 0)"
            :name="item.name"
            :description="item.description"
            />
        </template>
        <template v-if="this.technologyName === 'port'" v-for="(item, i) in technologyArr.technology">
            <TechnologyLaunch 
            :key="i"
            v-if="(i === 1)"
            :name="item.name"
            :description="item.description"
            />
        </template>
        <template v-if="this.technologyName === 'capsule'" v-for="(item, i) in technologyArr.technology">
            <TechnologyLaunch 
            :key="i"
            v-if="(i === 2)"
            :name="item.name"
            :description="item.description"
            />
        </template>
        <img v-if="this.technologyName === 'vehicle'" src="../assets/images/technology/image-launch-vehicle-portrait.jpg" alt="launch vehicle"/>
        <img v-if="this.technologyName === 'port'" src="../assets/images/technology/image-spaceport-portrait.jpg" alt="launch vehicle"/>
        <img v-if="this.technologyName === 'capsule'" src="../assets/images/technology/image-space-capsule-portrait.jpg" alt="launch vehicle"/>
    </main>
</template>

<script>
import axios from 'axios';
import TechnologyLaunch from '../components/TechnologyLaunch.vue';

export default {
    components: {
        TechnologyLaunch
    },
    data(){
        return {
            technologyName: 'vehicle',
            technologyArr: []
        }
    },
    created(){
        axios
            .get('data.json')
            .then(resp => {
                this.technologyArr = resp.data;
                console.log(this.technologyArr);
            })
    }
}
</script>

<style lang="scss" scoped>
.grid-container--technology {
    grid-template-areas: 
    'title'
    'content'
    'tabs'
    'image';
}

.grid-container--technology {
    .numbered-title {
        grid-area: title;
    }
    img {
        grid-area: image;
        max-width: 80%;
        margin-bottom: 2rem;
    }
    .numbered-indicators {
        grid-area: tabs;
    }
    .technology-info {
        grid-area: content;
    }
}

.numbered-indicators {
    gap: 2rem;
    button {
        width: 5rem;
        height: 5rem;
        border-radius: 50%;
        outline: none;
        background-color: transparent;
        border: 1px solid hsla(0, 0%, 100%, 1);
        color: hsl(0, 0%, 100%);
        cursor: pointer;
        &:hover {
            background-color: hsl(0,0,100%);
            color: hsl(0,0,0);
        }
        
    }
}

.numbered-indicators > [aria-selected="true"] {
    background-color: hsl(0,0,100%);
    color: hsl(0,0,0);
}


@media (min-width: 50em){
    .grid-container--technology {
        justify-items: start;
        text-align: left;
        grid-template-areas: 
        '. title title .'
        '. content image .'
        '. tabs image .';
    }
    .numbered-indicators {
        align-self: start;
    }
    .grid-container--technology > img {
        justify-self: end;
        max-width: 90%;
    }
}

</style>