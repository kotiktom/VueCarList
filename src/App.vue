<template>
<v-app>
  <v-app-bar app>
    <v-toolbar-title class="headline">
      <span>CARLIST</span>
    </v-toolbar-title>
    </v-app-bar>
<v-content>
<CarList />
</v-content>
</v-app>
</template>

<script>
import CarList from './components/CarList.vue'

export default {
  name: 'app',
  components: {
    CarList
  }
}
</script>

<style>

</style>
