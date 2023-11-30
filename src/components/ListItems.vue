<template>
    <ul role="list" class="divide-y divide-gray-100">
        <li v-for="item in items" :key="item.id" class="flex justify-between gap-x-6 py-5">
            <div class="flex min-w-0 gap-x-4">
                <img class="h-12 w-12 flex-none rounded-full bg-gray-50" :src="item.imageSrc" alt="" />
                <div class="min-w-0 flex-auto">
                    <p class="text-sm font-semibold leading-6 text-gray-900">{{ item.name }}</p>
                    <p class="mt-1 truncate text-xs leading-5 text-gray-500">{{ item.describe }}</p>
                </div>
            </div>
            <div class="hidden shrink-0 sm:flex sm:flex-col sm:items-end">
                <InputCounter></InputCounter>
            </div>
        </li>
    </ul>
</template>
  
<script>
import InputCounter from './InputCounter.vue'
export default {
    props: ['items'],
    components: {
        InputCounter
    },
    data() {
        return {
        }
    }
}


</script>