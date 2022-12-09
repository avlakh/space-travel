<template>
    <div 
        :class="{
            home : $route.path == '/', 
            destination: $route.path == '/destination',
            crew: $route.path == '/crew',
            technology: $route.path == '/technology'
            }">
        <SiteHeader/>
        <RouterView/>
    </div>
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