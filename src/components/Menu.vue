
<template>
    <div class="bg-white">
        <div class="mx-auto max-w-2xl px-10 lg:max-w-7xl ">

            <div class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8">
                <div v-for="product in products" :key="product.id" class="group relative" @click="SelectItem(product)">
                    <div class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-md bg-gray-200 lg:aspect-none group-hover:opacity-75 lg:h-60">
                        <img :src="product.imageSrc" :alt="product.imageAlt" class="h-full w-full object-cover object-center lg:h-full lg:w-full" />
                    </div>
                    <div class="mt-4 flex justify-between">
                        <div>
                            <h3 class="text-sm text-gray-700">
                                <a :href="product.href">
                                    <span aria-hidden="true" class="absolute inset-0" />
                                    {{ product.name }}
                                </a>
                            </h3>
                            <p class="mt-1 text-sm text-gray-500">{{ product.describe }}</p>
                        </div>
                        <p class="text-sm font-medium text-gray-900">{{ product.price }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            products: [

                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },
                {
                    id: 1,
                    name: 'Basic Tee',
                    imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
                    describe: "Front of men's Basic Tee in black.",
                    price: '$35'
                },

                // More products...
            ]
        }
    },
    methods: {
        submit() {
            this.$emit('someEvent')
        },
        SelectItem(item) {
            this.$emit('addItem', item)
        }
    }
}
</script>