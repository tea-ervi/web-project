<template>
    <header class = "z-[1100] flex flex-row text-[#0E2525] w-full items-center relative bg-gradient-to-l from-[#D5DEDA] to-[#0E2525]
    max-sm:justify-between max-sm:relative p-2">
        <div class = "basis-1/4 items-center justify-center px-8 min-w-40 max-sm:basis-auto">
            <img src="/assets/images/logo green.png" class = "w-16 h-16 bg-transparent">
        </div>
        <div class = "basis-1/4 max-sm:basis-auto">
        </div>
        <nav :class = "{'z-[1200] basis-1/2 flex flex-row items-center justify-end px-8 gap-4': !burger || burger,
            'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-white max-sm:px-0': burger,
            'max-sm:hidden': !burger}">
            <NuxtLink to = "/" class = "my-auto p-2 hover:text-[#577C7C] transition duration-300 max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">
                Coordinates
            </NuxtLink>
            <div class = "my-auto p-2 hover:bg-[#577C7C] hover:text-[#0E2525] transition duration-300 max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0" @click = "switch_submenu">Hydrology
                <div class = "flex flex-col absolute top-full bg-[#D5DEDA] text-[#577C7C] w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-[#D5DEDA] max-sm:text-[#577C7C]" v-show = "submenu">
                    <NuxtLink to = "/Lab3" class = "my-auto p-2 border-b-1 border-black hover:bg-[#86A9AC] hover:text-[#0E2525] max-sm:w-full max-sm:border-t-2 max-sm:text-center">Water level</NuxtLink>
                    <NuxtLink to = "/Lab4" class = "my-auto p-2 border-b-1 border-black hover:bg-[#86A9AC] hover:text-[#0E2525] max-sm:w-full max-sm:border-t-2 max-sm:text-center">Transparency</NuxtLink>
                    <NuxtLink to = "/Lab5" class = "my-auto p-2 border-b-1 border-black hover:bg-[#86A9AC] hover:text-[#0E2525] max-sm:w-full max-sm:border-t-2 max-sm:text-center">Temperature</NuxtLink>
                    <NuxtLink to = "/Lab6" class = "my-auto p-2 border-b-1 border-black hover:bg-[#86A9AC] hover:text-[#0E2525] max-sm:w-full max-sm:border-t-2 max-sm:text-center">Electrical conductivity</NuxtLink>
                </div>
            </div>
            <NuxtLink to = "/inform"
            :class = "{'my-auto p-2 hover:text-[#577C7C] transition duration-300 max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center': submenu,
                'my-auto p-2 hover:text-[#577C7C] transition duration-300 max-sm:w-full max-sm:border-b-2 max-sm:border-t-2 max-sm:border-black max-sm:text-center': !submenu}">
                Pathogens
            </NuxtLink>
        </nav>

        <div v-if = "!burger" @click = "switch_burger" class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
            <span class = "h-[3px] w-full bg-blue-950"></span>
            <span class = "h-[3px] w-full bg-blue-950"></span>
            <span class = "h-[3px] w-full bg-blue-950"></span>
        </div>
        <div v-else class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6" @click = "switch_burger">
            <span class = "h-[3px] w-full bg-blue-950 rotate-45 relative top-[9px]"></span>
            <span class = "h-[3px] w-full bg-blue-950 opacity-0"></span>
            <span class = "h-[3px] w-full bg-blue-950 relative bottom-3 rotate-[-45deg]"></span>
        </div>
    </header>

<main class = "z-[2] flex h-screen">
    <slot />
</main>

<footer class = "flex flex-row w-full bg-gradient-to-t from-[#577C7C] to-[#86A9AC] items-center justify-center px-4 py-8 gap-4">
    <a href = "https://www.youtube.com/"><img src="/assets/images/youtube.png" class = "w-20 h-16"></a>
    <a href = "https://github.com/"><img src="/assets/images/git.png" class = "w-16 h-16"></a>
    <a href = "https://www.facebook.com/login/"><img src="/assets/images/facebook.png" class = "w-16 h-16"></a>
</footer>
</template>



<script setup lang="ts">
import { useHead } from '#app';
import {ref} from 'vue'

const burger = ref<boolean>(false)
const submenu = ref<boolean>(false)

const switch_burger = ()=> {burger.value = !burger.value}
const switch_submenu = ()=> {submenu.value = !submenu.value}
console.log("default.vue loaded")
</script>

<!-- [#0E2525]
[#D5DEDA]
[#86A9AC]
[#71999C]
[#577C7C] -->