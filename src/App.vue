<template>
  <div id="app">
    <router-view />
    <FooterComponent v-if="showFooter" />
  </div>
</template>

<script>
import FooterComponent from "@/components/FooterComponent.vue";

export default {
  components: {
    FooterComponent,
  },
  data() {
    return {
      showFooter: true, // Atur kondisi awal sesuai kebutuhan
    };
  },
  watch: {
    // Memantau perubahan pada route
    $route() {
      // Lakukan pengecekan pada path route
      if (this.$route.name === "Tampilan404View") {
        this.showFooter = false; // Jika path adalah Tampilan404View, sembunyikan footer
      } else {
        this.showFooter = true; // Tampilkan footer untuk route lainnya
      }
    },
  },
};
</script>
