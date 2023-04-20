<script setup>
import {faker} from '@faker-js/faker';
</script>

<template>
    <div class="container mx-auto" style="height: 300vh">
        <h2>Inline & Block</h2>
        <div class="space-y-8">
            <div class="bg-red-500">Ceci est un élément block</div>
            <div class="bg-red-500 w-1/2">Ceci est un élément block</div>
            <span class="bg-green-200">Ceci est un élément inline</span>
            <span class="bg-green-200 ml-2 py-2 inline-block">Ceci est un élément 2e inline</span>
        </div>

        <h2>Positions</h2>
        <div class="static bg-red-500 mb-8">Element en position static</div>
        <div class="absolute top-0 left-0 bg-red-500 mb-8">Element en position absolute (top: 0; left: 0) sans parent
            relative
        </div>
        <div class="relative top-0 left-0 bg-green-500 mb-8 h-16">
            Element en position relative
            <div class="absolute top-0 left-0 bg-red-500">Element en position absolute (top: 0; left: 0) avec parent
                relative
            </div>
        </div>
        <div class="fixed top-0 right-0 bg-red-500">Element en position fixed (top: 0; right: 0)</div>
        <div class="sticky top-0 bg-red-500">Element en position sticky (top: 0)</div>


        <h2>Visibilité</h2>
        <div class="border border-black">
            <div class="hidden-element">
                Ceci est un élément caché via display: none;
            </div>
            <div class="invisible-element">
                Ceci est un élément caché via visibility: hidden;
            </div>
        </div>

        <h2>Grid</h2>
        <div class="items-grid">
            <div v-for="i in 8"
                 class="items-grid-element"
                 :style="`background-color: ${faker.color.rgb({ format: 'hex', casing: 'lower' })}`"
            >
            </div>
        </div>

        <h2>Flex</h2>
        <div class="items-flex mb-8">
            <div v-for="i in 3"
                 class="items-flex-element"
                 :style="`background-color: ${faker.color.rgb({ format: 'hex', casing: 'lower' })}`"
            >{{i}}</div>
        </div>
        <div class="items-flex">
            <div v-for="i in 48"
                 class="items-flex-element"
                 :style="`background-color: ${faker.color.rgb({ format: 'hex', casing: 'lower' })}`"
            ></div>
        </div>

        <h2>Axes</h2>
        <div class="flex">
            <div v-for="i in 5"
                 class="flex items-center justify-center text-3xl font-bold h-16 w-16 rounded-full -ml-4 shadow-md shadow-black/50"
                 :class="i === 3 ? 'z-10' : ''"
                 :style="`background-color: ${faker.color.rgb({ format: 'hex', casing: 'lower' })}`"
            >
                {{i === 3 ? '↑' : ''}}
            </div>
        </div>

        <h2>Texte tronqué</h2>
        <p class="truncate w-[25ch] bg-red-200 mb-8">
            {{ faker.lorem.paragraph(3) }}
        </p>
        <p class="w-1/2 bg-red-200" style="overflow-y: hidden; -webkit-box-orient: vertical; display: -webkit-box; -webkit-line-clamp: 3;">
            {{ faker.lorem.paragraph(8) }}
        </p>
    </div>
</template>

<style lang="postcss">
* {
    @apply transition-all duration-500;
}

h2 {
    @apply text-2xl mt-16 mb-8 border-t-2 first:border-t-0 pt-8 first:pt-0;
}

.items-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 3rem;
}

.items-grid-element {
    height: 50px;
}
.items-grid-element:nth-child(5) {
    grid-row: span 2;
}

.items-grid-element:nth-child(6) {
    width: 25px;
    height: 25px;
    justify-self: end;
    align-self: end;
}

.items-flex {
    display: flex;
    width: 100%;
    /*justify-content: flex-start;*/
    align-items: center;
    gap: 8px;
    flex-direction: column;
}

.items-flex-element {
    /*flex-grow: 1;*/
    width: 50px;
    height: 150px;
}
.items-flex-element:nth-child(3) {
    height: 50px;
    align-self: start;
}

.hidden-element {
    /*display: none;*/
}

.invisible-element {
    /*visibility: hidden;*/
}
</style>
