<template>
    <SiteHeader/>
    <RouterView/>
</template>

<script>

import SiteHeader from './components/SiteHeader.vue';

    export default {
    components: { 
        SiteHeader 
    }
}

</script>

<style lang="scss" scoped>

</style>