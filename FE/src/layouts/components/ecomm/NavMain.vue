<template>
  <vs-navbar :type="navbar.type" v-model="navbar.activeItem" class="nabarx justify-start">
    <vs-navbar-item index="0">
      <a class="text-lg" href="#">Home</a>
    </vs-navbar-item>

    <vs-navbar-item index="1">
      <a class="text-lg" href="#">News</a>
    </vs-navbar-item>

    <vs-navbar-item index="2">
      <a class="text-lg" href="#">Update</a>
    </vs-navbar-item>
  </vs-navbar>
</template>

<script>
export default {
  data () {

    return {
      navbar: {
        activeItem: 0,
        type: 'flat',
        types:
          [
            {
              value: null,
              text: 'Default'
            },
            {
              value: 'flat',
              text: 'Flat'
            },
            {
              value: 'fund',
              text: 'Fund'
            },
            {
              value: 'border',
              text: 'border'
            },
            {
              value: 'gradient',
              text: 'Gradient'
            },
            {
              value: 'shadow',
              text: 'Shadow'
            }
          ]
      }
    }
  }
}
</script>
