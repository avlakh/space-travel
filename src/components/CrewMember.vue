<template>
<article class="crew-info flow">
    <h2 class="ff-serif uppercase">{{position}}</h2>
    <p class="fs-700 uppercase ff-serif">{{name}}</p>
    <p>{{description}}</p>
</article>
</template>

<script>
export default {
    name: 'CrewMember',
    props: {
        position: {
            type: String,
            default: ''
        },
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

<style lang="scss" scoped>

</style>