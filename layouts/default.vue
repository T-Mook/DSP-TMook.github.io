<template>
  <v-app>
    <v-app-bar :color="appBar.color" max-height="50" dense flat>
      <v-spacer />
      <v-app-bar-title class="bar-title-text">
        {{ appBar.title }}
      </v-app-bar-title>
      <v-spacer />
    </v-app-bar>
    <v-container class="mb-4">
      <nuxt />
    </v-container>
    <main-footer />
  </v-app>
</template>

<script lang="ts">
import { Component, Provide, Vue } from 'nuxt-property-decorator'
import MainFooter from '@/components/default/MainFooter.vue'
@Component({
  components: {
    MainFooter,
  },
})
class LayoutDefault extends Vue {
  @Provide() appBar: { title: string; color: string } = {
    title: 'DYSON SPHERE PROGRAM 공장 최적화 도우미 (v.1.0.0)',
    color: 'rgba(21,31,32,1)',
  }
}
export default LayoutDefault
</script>

<style scoped>
.bar-title-text {
  font-size: 18px;
  color: white;
  font-weight: 900;
}
</style>
