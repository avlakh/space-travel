<template>
    <main class="grid-container grid-container--crew flow">
        <h1 class="numbered-title"><span aria-hidden="true">02</span>Meet your crew</h1>
        <div class="dot-indicators flex">
            <button 
                :aria-selected="true ? this.crewMem == 'com' : false"
                @click="this.crewMem = 'com'">
                <span class="sr-only">The commander</span></button>
            <button 
                :aria-selected="true ? this.crewMem == 'spec' : false"
                @click="this.crewMem = 'spec'">
                <span class="sr-only">The mission specialist</span></button>
            <button 
                :aria-selected="true ? this.crewMem == 'pilot' : false"
                @click="this.crewMem = 'pilot'">
                <span class="sr-only">The pilot</span></button>
            <button 
                :aria-selected="true ? this.crewMem == 'engine' : false"
                @click="this.crewMem = 'engine'">
                <span class="sr-only">The crew engineer</span></button>
        </div>
        <template v-if="this.crewMem === 'com'" v-for="(item, i) in peopleArr.crew">
            <CrewMember
                :key="i"
                v-if="(i === 0)"
                :position="item.role"
                :name="item.name"
                :description="item.bio"/>
        </template>
        <template v-if="this.crewMem === 'spec'" v-for="(item, i) in peopleArr.crew">
            <CrewMember
                :key="i"
                v-if="(i === 1)"
                :position="item.role"
                :name="item.name"
                :description="item.bio"/>
        </template>
        <template v-if="this.crewMem === 'pilot'" v-for="(item, i) in peopleArr.crew">
            <CrewMember
                :key="i"
                v-if="(i === 2)"
                :position="item.role"
                :name="item.name"
                :description="item.bio"/>
        </template>
        <template v-if="this.crewMem === 'engine'" v-for="(item, i) in peopleArr.crew">
            <CrewMember
                :key="i"
                v-if="(i === 3)"
                :position="item.role"
                :name="item.name"
                :description="item.bio"/>
        </template>
        <img v-if="this.crewMem === 'com'" src="../assets/images/crew/image-douglas-hurley.png" alt="Douglas Harley"/>
        <img v-if="this.crewMem === 'spec'" src="../assets/images/crew/image-mark-shuttleworth.png" alt="Mark Shuttleworth"/>
        <img  v-if="this.crewMem === 'pilot'" src="../assets/images/crew/image-victor-glover.png" alt="Victor Glover"/>
        <img  v-if="this.crewMem === 'engine'" src="../assets/images/crew/image-anousheh-ansari.png" alt="Anoushen Ansari"/>
    </main>
</template>

<script>
import axios from 'axios';
import CrewMember from '../components/CrewMember.vue';
export default {
    components: {
        name: CrewMember
    },
    data() {
        return {
            crewMem: "com",
            peopleArr: []
        };
    },
    components: { 
        CrewMember 
    },
    created() {
        axios
            .get('data.json')
            .then(resp => {
                this.peopleArr = resp.data;
                console.log(this.peopleArr)
            })
    }
}
</script>

<style lang="scss">

.grid-container--crew {
    grid-template-areas: 
    'title'
    'content'
    'tabs'
    'image';
}

.grid-container--crew {
    .numbered-title {
        grid-area: title;
    }
    img {
        grid-area: image;
        max-width: 60%;
        border-bottom: 1px solid hsla(0, 0%, 100%, 0.1);
    }
    .dot-indicators {
        grid-area: tabs;
    }
}

.crew-info {
    grid-area: content;
    padding: 2rem 0;
    h2 {
        opacity: .5;
    }
}

@media (min-width: 50em) {
    .grid-container--crew {
        justify-items: start;
        grid-template-areas: 
            '. title . .'
            '. content image .'
            '. tabs image .';
        .numbered-title {
            justify-self: left;
        }
    }
    .grid-container--crew img {
        max-width: 90%;
    }
    .grid-container--crew > .dot-indicators {
        justify-self: start;
    }
    .grid-container--crew > img {
        justify-self: end;
    }
}
</style>