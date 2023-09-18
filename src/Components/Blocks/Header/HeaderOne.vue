<template>
    <div :class="{ 'bg-gray-900 text-gray-100': block.data.darkMode, 'bg-white': !block.data.darkMode }">
        <div class="max-w-6xl mx-auto">
            <div class="flex justify-between items-center">
                <div>
                    <h1 class="text-[40px]">{{ block.data.title }}</h1>
                </div>
                <div  class="flex gap-x-4">
                    <div v-for="item, i in  block.data.list">
                        <nuxt-link :to="item.link">{{ item.text }}</nuxt-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'HeaderOne',
    props: {
        block: {
            type: Object,
            required: true,
        },
        first: {
            type: Boolean,
            default: false
        },
    },
    setup() {

    },
})
</script>
