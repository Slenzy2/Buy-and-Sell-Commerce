<template>
  <q-layout view="lhh LpR lFf">
    <q-header style="background-color: white">
      <div class="row">
        <SellerDashboard @toggleLeftDrawer="toggleLeftDrawer" />
      </div>
    </q-header>

    <q-drawer
      side="left"
      v-model="leftDrawerOpen"
      show-if-above
      :width="230"
      class="drawer text-white bg-primary"
      :breakpoint="830"
    >
      <q-list>
        <EssentialLink />
      </q-list>
    </q-drawer>

    <q-footer class="absolute-bottom">
      <div class="bg-primary">
        <div
          class="q-mr-md text-center q-py-xs text-weight-bold text-white"
          style=""
        >
          ©Buy and Sell
        </div>
      </div>
    </q-footer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "src/components/Seller/SellerEssentialLink.vue";
import SellerDashboard from "components/Navbars/sellerDashboard.vue";

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
    SellerDashboard,
  },

  data() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },

      sellerToken: localStorage.getItem("sellerToken"),
      buyerToken: localStorage.getItem("buyerToken"),
      username: ref(""),
    };
  },
  // methods: {
  //   getSeller() {
  //     let id = localStorage.getItem("sellerId");
  //     this.$store
  //       .dispatch("moduleExample/getSingleSeller", id)
  //       .then((response) => {
  //         console.log(response);
  //         this.$store.commit("moduleExample/seller", response);
  //       });
  //   },
  //   getOrders() {
  //     this.$store.dispatch("moduleExample/getSellerOrders");
  //   },
  // },
  // mounted() {
  //   this.getSeller();
  //   this.getOrders();
  // },
});
</script>

<style scoped></style>
