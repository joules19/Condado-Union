<template>
  <div>
    <main>
      <section class="relative w-full h-full py-40 min-h-screen">
        <div
          class="absolute top-0 w-full h-full bg-blueGray-800 bg-repeat bg-full"
          :style="`background-image: url('${registerBg2}');`"
          style="opacity: 0.8"
        ></div>
        <router-view />
      </section>
    </main>
  </div>
</template>
<script>
// import Navbar from "@/components/Navbars/AuthNavbar.vue";
// import FooterSmall from "@/components/Footers/FooterSmall.vue";

import registerBg2 from "@/assets/img/deutsche-bank.jpg";

export default {
  data() {
    return {
      registerBg2,
    };
  },
  components: {
    // Navbar,
    // FooterSmall,
  },
};
</script>
