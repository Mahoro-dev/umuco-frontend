<template>
  <div
    class="mx-auto max-w-2xl px-24 py-16 sm:px-6 sm:py-12 lg:max-w-7xl lg:px-8"
  >
    <div class="flex justify-between items-center">
      <h2 class="text-2xl font-bold tracking-tight text-gray-900">
        {{ message }}
      </h2>
      <input
        type="text"
        :value="search"
        @input="$emit('search', $event.target.value)"
        placeholder="Search"
        class="border border-gray-300 rounded-md px-4 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500"
      />
    </div>

    <div
      class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8"
    >
      <div
        class="w-full max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-white dark:border-gray-700"
        v-for="(row, i) in filteredData"
        :key="i"
      >
        <a href="#">
          <img
            class="p-5 rounded-t-lg"
            :src="`/assets/img/` + row.image"
            alt="product image"
          />
        </a>
        <div class="px-5 pb-2">
          <a href="#">
            <h5
              class="text-sm font-semibold tracking-tight text-gray-900 dark:text-gray-500"
            >
              {{ row.title }}
            </h5>
          </a>
          <div class="flex items-center justify-between">
            <span class="text-xl font-bold text-gray-900 dark:text-gray-800">
              {{ row.price }} Rwf
            </span>
            <a
              href="#"
              class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
              >View more</a
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    search: {
      type: String,
      default: "", // Default value for search
    },
    tab: {
      type: Number,
      default: 0, // Default value for tab
    },
    data: {
      type: Array,
      default: () => [
        { id: "", title: "", image: "", price: "" },
      ], // Default value for data
    },
    message: {
      type: String,
      default: "", // Default value for message
    },
  },
  computed: {
    filteredData() {
      const query = this.search.toLowerCase();
      return this.data.filter((item) =>
        item.title.toLowerCase().includes(query)
      );
    },
  },
};
</script>
