<template>
  <div id="hp">
    Core Home
  </div>
</template>

<script>
import Meta from 'core/lib/meta'
import MainSlider from 'core/components/blocks/MainSlider/MainSlider.vue'
import ProductTile from 'core/components/ProductTile.vue'

export default {
  name: 'Home',
  meta: {
    title: 'Home Page'
  },
  beforeMount () {
    this.$store.dispatch('category/reset')

    if (global.__DEMO_MODE__) {
      this.$store.dispatch('claims/check', { claimCode: 'onboardingAccepted' }).then((onboardingClaim) => {
        if (!onboardingClaim) { // show onboarding info
          this.$bus.$emit('modal-toggle', 'modal-onboard')
          this.$store.dispatch('claims/set', { claimCode: 'onboardingAccepted', value: true })
        }
      })
    }
  },
  components: {
    ProductTile,
    MainSlider
  },
  mixins: [Meta]
}
</script>
