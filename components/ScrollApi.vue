<template>
    <div
      class="mx-auto max-w-2xl px-4 py-8 sm:px-6 sm:py-12 lg:max-w-7xl lg:px-8"
    >
      <h2 class="text-2xl font-bold tracking-tight text-gray-900 mb-6">Infinite Scroll</h2>
      <div
        id="content"
        class="grid grid-cols-1 gap-y-6 sm:grid-cols-2 sm:gap-x-6 lg:grid-cols-3 lg:gap-x-8"
      >
        <div
          v-for="item in items"
          :key="item.id"
          class="p-4 bg-white border rounded shadow text-gray-700"
        >
          {{ item.name }}
        </div>
      </div>
      <div
        v-if="loading"
        id="loading"
        class="mt-6 text-center text-gray-500"
      >
        Loading...
      </div>
    </div>
  </template>
<script>
export default {
  data() {
    return {
      items: [], // Holds the items to display
      currentPage: 1, // Current page of data
      loading: false, // Show loading indicator
    };
  },
  methods: {
    async fetchItems() {
      this.loading = true;

      // Simulate API call with a delay (replace with actual API call)
      await new Promise((resolve) => setTimeout(resolve, 1000));

      // Simulate new data (replace this with API response data)
      const newItems = Array.from({ length: 50 }, (_, i) => ({
        id: this.items.length + i + 1,
        name: `Item ${this.items.length + i + 1}`,
      }));

      this.items.push(...newItems);
      this.loading = false;
    },
    onScroll() {
      const scrollContainer = document.documentElement;
      const scrollTop = scrollContainer.scrollTop;
      const scrollHeight = scrollContainer.scrollHeight;
      const clientHeight = scrollContainer.clientHeight;

      // Check if the user is near the bottom of the page
      if (scrollTop + clientHeight >= scrollHeight - 10 && !this.loading) {
        this.fetchItems();
      }
    },
  },
  mounted() {
    // Fetch initial items
    this.fetchItems();

    // Add scroll listener
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    // Remove scroll listener
    window.removeEventListener("scroll", this.onScroll);
  },
};
</script>
  