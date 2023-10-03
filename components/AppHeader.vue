<template>

    <header class="header">
        <div class="container">
            <div class="header-flex">
                <nuxt-link class="logo" to="/">
                    <img src="/logo/logo.svg" alt="">
                </nuxt-link>

                <div @click="isActive = !isActive" :class="{'bg-btn': isActive}" class="menu-btn">
                    <div class="part1"></div>
                    <div class="part2"></div>
                    <div class="part3"></div>
                </div>

                <div class="head-info">
        
                    <div class="side-icon-box" v-for="box in headInfo">
                        <div class="icon">
                            <img :src="'/logo/' + box.icon " alt="">
                        </div>
                        <div class="content">
                            <span>{{ box.title }}</span>
                            <nuxt-link :to="box.to">
                                {{ box.text }}
                            </nuxt-link>
                        </div>
                    </div>
        
                </div>
            </div>
            <nav class="header-nav">
                <nuxt-link class="header-nav-item" v-for="nav in headNav" :to="{to: nav.to, hash: nav.hash}">
                    {{ nav.name }}
                </nuxt-link>
            </nav>
        </div>
        <transition name="appear">
                <nav v-show="isActive" class="header-mob-nav">
                    <div class="container">
                        <div class="menu header-mob-flex">
                            <nuxt-link @click="isActive = false" class="header-mob-nav-item" v-for="nav in headNav" :to="{to: nav.to, hash: nav.hash}">
                                {{ nav.name }}
                            </nuxt-link>
                        </div>
                    </div>
                </nav>
        </transition>
    </header>
</template>

<script setup>
import {ref} from 'vue'

const isActive = ref(false)


const headInfo = [
    {icon: "home.svg", title: "Адрес", text: "ул.Куусинена, д.21Б, оф.318", to: "https://yandex.ru/maps/-/CDU9UMLk"},
    {icon: "phone.svg", title: "Позвонить нам", text: "+7 (495) 783-68-53", to: "tel:+74957836853"},
    {icon: "envelope.svg", title: "Эл. почта", text: "info@vzdv.ru", to: "mailto:info@vzdv.ru"}
]

const headNav = [
    {name: "Главная", to: "/", hash: ""},
    {name: "Преимущества", to: "/", hash: "#advantages"},
    {name: "Проекты", to: "/", hash: "#project"},
    {name: "Наши клиенты", to: "/", hash: "#clients"},
    {name: "Контакты", to: "/", hash: "#contact"}
]

watchEffect(() => {
    useHead({
        bodyAttrs: {
            class: isActive.value ? '_lock' : ''
        }
    })
})

</script>

<style lang="scss">
._lock {
    overflow: hidden;
}

.header {
    background-color: $text-header;
    position: sticky;   
    top: 0;
    width: 100%;
    left : 0;
    z-index : 50;

    @media only screen and (min-width: 1280px) {
        position: relative;
    }
}

.appear-enter-active {
    animation: showMob .5s;
}

.appear-leave-active {
    animation: hidMob .5s;
}

@keyframes showMob {
    0% {
        max-height: 0;
    }
    100% {
        max-height: 100%;
    }
}

@keyframes hidMob {
    0% {
        max-height: 100%;
    }
    100% {
        max-height: 0;
    }
}

.header-mob-nav {
    width: 100%;
    height: 100%;
    position: fixed;
    overflow: hidden;
    z-index : 50;

    background-color: $bg-header;

    @media only screen and (min-width: 1280px) {
        display: none;
    }

    .header-mob-flex {
        display: flex;
        flex-direction: column;
        justify-content: left;

        gap: 20px;
    }

    .menu {
        padding: 30px 0;
    }

    .header-mob-nav-item {
        display: block;
        font-family: "Montserrat";
        text-transform: uppercase;

        color: $text-header;
        text-decoration: none;

        &:hover {
            color: $bg;
        }
    }
}

.header-flex {

    padding: 30px 0;

    display: flex;
    justify-content: space-between;
    align-items: center;

    @media only screen and (max-width: 1279px) {
        padding: 17px 0;
    }
}

.menu-btn {
    display: none;

    position: relative;
    width: 30px;
    height: 30px;
    border-radius: 4px;
    cursor: pointer;
    -webkit-transition: background-color 0.25s;
    transition: background-color 0.25s;

    background-color: $bg-header;

    @media (max-width: 1280px) {
        display: block;
    }

    & > div {
        position: absolute;
        left: 7.5px;
        width: 15px;
        height: 2px;
    }

    .part1 {
        top: 9px;
        background: $text-header;
    }

    .part2 {
        top: 14px;
        background: $text-header;
    }

    .part3 {
        bottom: 9px;
        background: $text-header;
    }
}

.bg-btn {
    background-color: $bg;
}

.head-info {
    display: flex;
    flex-direction: row;
    gap: 30px;

    @media (max-width: 1280px) {
        display: none;
    }
}

.side-icon-box {
    display: flex;
    flex-direction: row;

    gap: 10px;

    .icon {
        background-color: $bg;
        width: 50px;
        height: 50px;
        box-shadow: 0 0 5px 1px rgba(0, 0, 0, 0.1);


        display: flex;
        justify-content: center;
        align-items: center;
    }

    .content {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
    }
}

.isVis {
    display: block;
}

.header-nav {
    position: absolute;
    z-index: 20;
    width: 100%;
    max-width: 1180px;

    display: flex;
    justify-content: center;
    gap: 40px;
    background-color: $bg-header;
    padding: 24.5px 20px;
    

    @media (max-width: 1280px) {
        display: none;
    }


    .header-nav-item {
        font-family: "Montserrat";
        text-transform: uppercase;

        color: $text-header;
        text-decoration: none;

        &:hover {
            color: $bg;
        }
    }
}


</style>