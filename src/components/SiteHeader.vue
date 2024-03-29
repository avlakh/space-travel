<template>
    <header class="primary-header flex">
        <div class="primary-logo">
            <router-link to="/">
                <img src="../assets/images/shared/logo.svg" alt="space tourism logo" class="logo">
            </router-link>
        </div>
        <button class="mobile-nav-toggle" :aria-expanded="'true' ? isMobileMenuOpened : 'false'" @click="toggleMobileMenu"><span class="sr-only">Menu</span></button>
        <nav>
            <ul :data-visible="'false' ? isMobileMenuOpened : 'true'" class="primary-navigation underline-indicators flex" :class="{'mob-nav-transform': isMobileMenuOpened}">
                <li :class="{active: $route.path == '/'}">
                    <router-link class="ff-sans-cond uppercase text-white letter-spacing-2" to="/" @click="toggleMobileMenu"><span aria-hidden="true">00</span>Home</router-link>
                </li>
                <li :class="{active: $route.path == '/destination'}">
                    <router-link class="ff-sans-cond uppercase text-white letter-spacing-2" to="/destination" @click="toggleMobileMenu"><span aria-hidden="true">01</span>Destination</router-link>
                </li>
                <li :class="{active: $route.path == '/crew'}">
                    <router-link class="ff-sans-cond uppercase text-white letter-spacing-2" to="/crew" @click="toggleMobileMenu" ><span aria-hidden="true">02</span>Crew</router-link>
                </li>
                <li :class="{active: $route.path == '/technology'}">
                    <router-link class="ff-sans-cond uppercase text-white letter-spacing-2" to="/technology" @click="toggleMobileMenu" aria-hidden="true"><span>03</span>Technology</router-link>
                </li>
            </ul>  
        </nav>
    </header>
</template>

<script>

import {RouterLink} from 'vue-router';

export default {
    data (){
        return {
            isMobileMenuOpened: false
        }
    },
    methods: {
        toggleMobileMenu(){
            this.isMobileMenuOpened = !this.isMobileMenuOpened;
            const el = document.querySelector('.mobile-nav-toggle');
            const attr = el.getAttribute('aria-expanded');
            if (window.innerWidth < 800) {
                attr === 'false' ? document.body.classList.add('hidden') : document.body.classList.remove('hidden');
            }
        }
    }
}
</script>

<style lang="scss" scoped>

.primary-header {
    padding: 2rem 4rem;
    align-items: center;
    justify-content: space-between;
}

.primary-navigation {
    gap: 1rem;
    list-style: none;
    padding: 8px 20px;
    margin: 0;
    background-color: hsl(230, 35%, 7%, 1);
    transition: transform 0.2s ease-in-out;
    position: relative;
    &::after {
        content: '';
        position: absolute;
        height: 1px;
        top: 49%;
        left: -73%;
        width: 75%;
        background: hsl(0deg, 0%, 100%, .25);
    }
    a {
        text-decoration: none;
        display: block;
        width: 100%;
        height: 100%;
        padding: 1rem 0;
        span {
            font-weight: 700;
            margin-right: .5em;
        }
    }
}

.primary-logo {
    cursor: pointer;
}

// to perform a check whether browser supports it
@supports (backdrop-filter: blur(1rem)) {
    .primary-navigation {
        background-color: hsl(230, 35%, 7%, 0.5);
        backdrop-filter: blur(1rem);
    }
}

.mobile-nav-toggle {
    display: none;
}

.primary-navigation[data-visible="true"] {
    transform: translateX(0%);
}

.mobile-nav-toggle[aria-expanded="true"] {
    background-image: url(../assets/images/shared/icon-close.svg);
}

/* media queries */

@media (max-width: 90em) {
    .primary-navigation::after {
        content: none;
    }
}

@media (max-width: 50em){
    .primary-header {
        padding: 2rem;
    }
    .primary-navigation {
        gap: 2rem;
        list-style: none;
        inset: 0 0 0 20%;
        z-index: 1000;
        padding: min(20rem, 15vh) 2rem;
        margin: 0;
        position: fixed;
        flex-direction: column;
        transform: translateX(100%);
    }
    .primary-navigation.underline-indicators > .active {
        border: 0;
    }
    .mobile-nav-toggle {
        display: block;
        position: absolute;
        z-index: 2000;
        top: 2.25rem;
        right: 2rem;
        background: transparent;
        background-image: url(../assets/images/shared/icon-hamburger.svg);
        background-repeat: no-repeat;
        background-position: center;
        width: 1.5rem;
        aspect-ratio: 1;
        border: 0;
    }
}

</style>