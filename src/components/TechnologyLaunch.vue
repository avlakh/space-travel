<template>
    <article class="technology-info flow">
        <h2 class="ff-serif uppercase">The terminology...</h2>
        <p class="fs-700 uppercase ff-serif">{{name}}</p>
        <p>{{description}}</p>
    </article>
</template>

<script>
export default {
    name: 'TechnologyLaunch',
    props: {
        name: {
            type: String,
            default: ''
        },
        description: {
            type: String,
            default: ''
        }
    }
}
</script>

<style lang="scss">

</style>