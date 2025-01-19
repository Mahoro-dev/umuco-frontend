<template>
  <div>
    <div class="bg-white py-6 sm:py-12">
      <div class="mx-auto max-w-7xl px-3 lg:px-8">
        <div
          class="text-sm font-medium text-center text-gray-500 border-b border-gray-200 dark:text-gray-400 dark:border-gray-700"
        >
          <ul class="flex flex-wrap -mb-px">
            <li class="me-2">
              <span
                @click="changeTab(1)"
                :class="
                  tab === 1
                    ? 'inline-block p-4 text-blue-600 border-b-2 border-blue-600 rounded-t-lg dark:text-blue-500 dark:border-blue-500'
                    : 'inline-block p-4 text-gray-500 border-b-2 border-transparent hover:text-blue-600 hover:border-blue-600 rounded-t-lg dark:text-gray-400 dark:hover:text-blue-500'
                "
              >
                Stationery Essentials
              </span>
            </li>
            <li class="me-2">
              <span
                @click="changeTab(2)"
                :class="
                  tab === 2
                    ? 'inline-block p-4 text-blue-600 border-b-2 border-blue-600 rounded-t-lg dark:text-blue-500 dark:border-blue-500'
                    : 'inline-block p-4 text-gray-500 border-b-2 border-transparent hover:text-blue-600 hover:border-blue-600 rounded-t-lg dark:text-gray-400 dark:hover:text-blue-500'
                "
              >
                Textbooks and Workbooks
              </span>
            </li>
            <li class="me-2">
              <span
                @click="changeTab(3)"
                :class="
                  tab === 3
                    ? 'inline-block p-4 text-blue-600 border-b-2 border-blue-600 rounded-t-lg dark:text-blue-500 dark:border-blue-500'
                    : 'inline-block p-4 text-gray-500 border-b-2 border-transparent hover:text-blue-600 hover:border-blue-600 rounded-t-lg dark:text-gray-400 dark:hover:text-blue-500'
                "
              >
                School Bags and Backpacks
              </span>
            </li>
            <li class="me-2">
              <span
                @click="changeTab(4)"
                :class="
                  tab === 4
                    ? 'inline-block p-4 text-blue-600 border-b-2 border-blue-600 rounded-t-lg dark:text-blue-500 dark:border-blue-500'
                    : 'inline-block p-4 text-gray-500 border-b-2 border-transparent hover:text-blue-600 hover:border-blue-600 rounded-t-lg dark:text-gray-400 dark:hover:text-blue-500'
                "
              >
                Health and Safety Items
              </span>
            </li>
            <li class="me-2">
              <span
                @click="changeTab(5)"
                :class="
                  tab === 5
                    ? 'inline-block p-4 text-blue-600 border-b-2 border-blue-600 rounded-t-lg dark:text-blue-500 dark:border-blue-500'
                    : 'inline-block p-4 text-gray-500 border-b-2 border-transparent hover:text-blue-600 hover:border-blue-600 rounded-t-lg dark:text-gray-400 dark:hover:text-blue-500'
                "
              >
                Exam and Study Aids
              </span>
            </li>
          </ul>
        </div>
      </div>

      <!--tab content-->
      <CategoryTab
        @search="search($event)"
        :search="searchQuery"
        :message="message"
        :tab="1"
        :data="tabData"
      />
    </div>
  </div>
</template>

<script>
import CategoryTab from "./categories/CategoryTab.vue";
export default {
  components: { CategoryTab },
  data() {
    return {
      tab: 1,
      searchQuery: "",
      message: "Stationery Essentials",
      tabData: [
        {
          id: 1,
          title: "Cahiers piqués quad.5mm + marge bleu",
          price: 5000,
          image: "36mt.png",
        },
        {
          id: 1,
          title: "Cahiers piqués travers 8mm + marge bleu",
          price: 8000,
          image: "60MQ5.jpg",
        },
        {
          id: 1,
          title: "Sachet 6 pinceaux scolaires ronds série 101 nº 16",
          price: 56000,
          image: "36MQ5.jpg",
        },
        {
          id: 1,
          title: "Boîte de 6 pots de gouache de 25 ml couleurs assorties",
          price: 3400,
          image: "80304B_01.jpg",
        },
        {
          id: 1,
          title: "Album de Présentation 50 pochettes ",
          price: 5000,
          image: "photo1.jpg",
        },
        {
          id: 1,
          title: "bouteille de Gouache de 1000 ml outre-mer",
          price: 5000,
          image: "D102CDQ5.jpg",
        },
        {
          id: 1,
          title: "Cahiers piqués quad.5mm + marge bleu",
          price: 5000,
          image: "74.00.37.jpg",
        },
        {
          id: 1,
          title: "Cahiers piqués quad.5mm + marge bleu",
          price: 5000,
          image: "36mt.png",
        },
        {
          id: 1,
          title: "Cahiers piqués quad.5mm + marge bleu",
          price: 5000,
          image: "36mt.png",
        },
        {
          id: 1,
          title: "Cahiers piqués travers 8mm + marge bleu",
          price: 8000,
          image: "60MQ5.jpg",
        },
        {
          id: 1,
          title: "Sachet 6 pinceaux scolaires ronds série 101 nº 16",
          price: 56000,
          image: "36MQ5.jpg",
        },
        {
          id: 1,
          title: "Boîte de 6 pots de gouache de 25 ml couleurs assorties",
          price: 3400,
          image: "80304B_01.jpg",
        },
      ],
    };
  },
  methods: {
    search(query) {
      this.searchQuery = query;
      query = this.searchQuery.toLowerCase();
      return this.tabData.filter((item) =>
        item.title.toLowerCase().includes(query)
      );
    },
    changeTab(tab) {
      this.tab = tab;
      if (tab == 1) {
        this.message = "Stationery Essentials";
      } else if (tab == 2) {
        this.message = "Textbooks and Workbooks";
      } else if (tab == 3) {
        this.message = "School Bags and Backpacks";
      } else if (tab == 4) {
        this.message = "Health and Safety Items";
      }
      ("Textbooks and Workbooks");
    },
  },
};
</script>
