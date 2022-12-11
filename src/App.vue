<template>
    <div 
        :class="{
            home : $route.path == '/', 
            destination: $route.path == '/destination',
            crew: $route.path == '/crew',
            technology: $route.path == '/technology'
            }">
        <SiteHeader/>
        <RouterView v-slot="{Component}">
            <Transition name="route" mode="out-in">
                <component :is="Component"></component>
            </Transition>
        </RouterView>
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
.route-enter-active,
.route-leave-active {
  transition: opacity 0.5s ease;
}

.route-enter-from,
.route-leave-to {
  opacity: 0;
}
</style>