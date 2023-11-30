
<template>
  <div>
    <div class="bg-white">
      <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
        <h2 class="text-2xl font-bold tracking-tight text-gray-900">Danh sach ban</h2>

        <div class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8">
          <div data-modal-target="large-modal" data-modal-toggle="large-modal" v-for="table in tables" :key="table.id" class="group relative" @click="openDetail(table)">
            <button data-modal-target="large-modal" style="display: none;" data-modal-toggle="large-modal" class="block w-full md:w-auto text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800" type="button">
    Large modal
    </button>
            <div class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-md bg-gray-200 lg:aspect-none group-hover:opacity-75 lg:h-80">
              <img :src="table.imageSrc" class="h-full w-full object-cover object-center lg:h-full lg:w-full" />
            </div>
            <div class="mt-4 flex justify-between">
              <div>
                <h3 class="text-sm text-gray-700">
                  <a>
                    <span aria-hidden="true" class="absolute inset-0" />
                    {{ table.tableName }}
                  </a>
                </h3>
                <p class="mt-1 text-sm text-gray-500">{{ table.Describe }}</p>
              </div>
              <p class="text-sm font-medium text-gray-900">{{ table.price }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>


    <!-- Large Modal -->
    <div id="large-modal" tabindex="-1" class="fixed top-0 left-0 right-0 z-50 hidden w-full p-4 overflow-x-hidden overflow-y-auto md:inset-0 h-[calc(100%-1rem)] max-h-full">
      <div class="relative w-full max-w-7xl max-h-full">
        <!-- Modal content -->
        <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
          <!-- Modal header -->
          <div class="flex items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600">
            <h3 class="text-xl font-medium text-gray-900 dark:text-white">
              Large modal
            </h3>
            <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ms-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white" data-modal-hide="large-modal">
              <svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6" />
              </svg>
              <span class="sr-only">Close modal</span>
            </button>
          </div>
          <!-- Modal body -->
          <div class="p-4 md:p-5 space-y-4 flex">
            <div class="shrink-0">
              <ListItems :items="tableData" />
              <button @click="printRawHtml" type="button" class="text-white w-full bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Print</button>
            </div>
            <div>
              <Menu @add-item="addItem" />
            </div>

            
          </div>
          <!-- Modal footer -->
          <div class="flex items-center p-4 md:p-5 space-x-3 rtl:space-x-reverse border-t border-gray-200 rounded-b dark:border-gray-600">
            <button data-modal-hide="large-modal" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">I accept</button>
            <button data-modal-hide="large-modal" type="button" class="ms-3 text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-gray-200 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600">Decline</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Modal } from 'flowbite'
import ListItems from '../components/ListItems.vue'
import Menu from '../components/Menu.vue'
import printJS from 'print-js'
export default {
  components: {
    ListItems,
    Menu
  },
  data() {
    return {
      tables: [

        {
          id: 1,
          tableName: 'Ban 1',
          imageSrc: 'data:image/jpeg;base64,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',
          Describe: "Ban doi 2 nguoi.",
          price: '$35',
          orders: [
            {
              id: 1,
              name: 'Basic Tee',
              imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
              describe: "Front of men's Basic Tee in black.",
              price: '$35',
              count: 1,
              totalPrice: '$35',
            }, {
              id: 1,
              name: 'Basic Tee',
              imageSrc: 'https://gongcha.com.vn/wp-content/uploads/2022/06/Tra-sua-tran-chau-HK.png',
              describe: "Front of men's Basic Tee in black.",
              price: '$35',
              count: 1,
              totalPrice: '$35',
            },
          ]
        },

        // More products...
      ],
      tableData: []
    }
  },
  methods: {
    openDetail(table) {
        this.tableData = table.orders;
    },
    addItem(item) {
      this.tableData.push(item)
    },
    printRawHtml() {
      printJS({
        printable: `<h1>Print.js Raw HTML Print Test</h1>
        <p class="blueText">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
        <p>sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>`,
        type: 'raw-html',
        header: 'JSON Print Header',
        footer: 'JSON Print Footer',
        style: '.blueText {color:blue;}'
      })
    }
  }
}

</script>
