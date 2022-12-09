<template>
    <article class="destination-info">
        <h2 class="fs-800 uppercase ff-serif">{{name}}</h2>
        <p>{{description}}</p>
        <div class="destination-meta flex">
            <div>
                <h3 class="text-accent fs-200 uppercase">Avg. distance</h3>
                <p class="ff-serif uppercase">{{distance}}</p>
            </div>
            <div>
                <h3 class="text-accent fs-200 uppercase">Est. travel time</h3>
                <p class="ff-serif uppercase">{{travel}}</p>
            </div>
        </div>
    </article>
</template>

<script>

export default {
    name: 'DestinationPlanet',
    props: {
        name: {
            type: String,
            default: ''
        },
        description: {
            type: String,
            default: ''
        },
        distance: {
            type: String,
            default: ''
        },
        travel: {
            type: String,
            default: ''
        }
    }
}
</script>

<style lang="scss" scoped>
.destination-info {
    grid-area: content;
}

.destination-meta {
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    border-top: 1px solid hsla(0, 0%, 100%, 0.1);
    padding: 2.5rem 0;
    margin-top: 2.5rem;
    p {
        font-size: 1.75rem;
    }
}

@media (min-width: 50em){
    .destination-meta {
        flex-direction: row;
        justify-content: space-evenly;
    }
}

</style>