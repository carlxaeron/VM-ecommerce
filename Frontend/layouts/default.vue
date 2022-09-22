<template>
  <div>
    <HeaderContainer />
    <Nuxt />
    <Footer />
  </div>
</template>

<script>
import HeaderContainer from '../container/HeaderContainer.vue';
import Footer from '~/container/Footer.vue';
export default {
  name: "DefaultLayout",
  components: { Footer, HeaderContainer }
}
</script>
