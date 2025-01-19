<template>
  <div class="bg-white">
    <!-- <ScrollApi/> -->
    <!--Home section-->
    <Home />
    <!--Categories section-->
    <CategoriesSection />
    <!--Contact section-->
    <Contact />
    <!--Client section-->
    <ClientSection />
  </div>
</template>
<script>
definePageMeta({
  layout: "default",
});
import ScrollApi from "~/components/ScrollApi.vue";
import Contact from "~/components/Contact.vue";
import Home from "~/components/Home.vue";
import CategoriesSection from "~/components/CategoriesSection.vue";
import ClientSection from "~/components/ClientSection.vue";
export default {
  components: {
    Contact,
    Home,
    CategoriesSection,
    ClientSection,
    ScrollApi
  },
  data() {
    return {
      tab: 1,
    };
  },
};
</script>
