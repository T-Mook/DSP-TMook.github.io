<template>
  <v-row justify="center" align="center">
    <v-card
      :max-width="mainCardMaxWidth"
      :min-height="$vuetify.breakpoint.height - 122"
      color="rgba(0,0,0,0)"
    >
      <v-card-text class="d-flex justify-center mt-4 pb-0 yellow--text">
        {{ textOfGoal }}
      </v-card-text>
      <!-- ### Start : Search Bar ### -->
      <v-card-actions class="d-flex justify-center">
        <v-card flat max-width="400" class="mt-4 py-0">
          <v-autocomplete
            v-model="resourceName"
            :items="totalNameOfResource"
            dense
            filled
            hide-details
            label="생산 목표 자원"
          ></v-autocomplete>
        </v-card>
      </v-card-actions>
      <!-- ### Start : All Required Process ### -->
      <required-process :upper-resource-name="resourceName" />
      <v-card-actions class="justify-center my-2">
        <v-btn
          href="https://store.steampowered.com/app/1366540/Dyson_Sphere_Program/"
          color="blue lighten-1"
          outlined
        >
          Buy Here! (
          <v-icon small class="mr-1">mdi-steam</v-icon>
          Steam)
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-row>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import RequiredProcess from '@/components/index/RequiredProcess.vue'
import dataEnSample from '~/static/data/dataEn.json'

@Component({
  head() {
    return {
      title: '공정 최적화 도우미 - Dyson Sphere Program w T-Mook',
    }
  },
  asyncData() {
    const totalNameOfResource: Array<string> = Object.keys(dataEnSample)
    return { totalNameOfResource }
  },
  components: {
    RequiredProcess,
  },
  computed: {
    mainCardMaxWidth(): number {
      const maxWidth: number =
        this.$vuetify.breakpoint.width < 860
          ? this.$vuetify.breakpoint.width
          : 860
      return maxWidth
    },
  },
})
class PagesIndex extends Vue {
  textOfGoal: string = "'어떻게 하면 이 자원을 끊김없이 생산할까?'"
  resourceName: null | string = 'Electric Motor'
}
export default PagesIndex
</script>

<style scoped>
#app
  > div
  > div
  > div
  > div
  > div
  > div:nth-child(1)
  > div
  > div.v-card__actions
  > a {
  text-transform: none;
}
</style>
