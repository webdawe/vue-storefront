<template>
  <button>
    Core price button
  </button>
</template>

<script>
export default {
  name: 'PriceButton',
  props: {
    content: {
      type: null,
      default: ''
    },
    id: {
      type: null,
      required: true
    },
    code: {
      type: null,
      required: true
    },
    from: {
      type: null,
      required: true
    },
    to: {
      type: null,
      required: true
    },
    context: {
      type: null,
      default: ''
    }
  },
  data () {
    return {
      active: false
    }
  },
  beforeDestroy () {
    this.$bus.$off('filter-reset')
    this.$bus.$off('filter-changed-' + this.context)
  },
  beforeMount () {
    this.$bus.$on('filter-reset', (filterOption) => {
      this.active = false
    })
    this.$bus.$on('filter-changed-' + this.context, (filterOption) => {
      if (filterOption.attribute_code === this.code) {
        if (filterOption.id === this.id) {
          if (this.active) {
            this.active = false
          } else {
            this.active = true
          }
        } else {
          this.active = false
        }
        // filterOption.id === this.id ? this.active = true : this.active = false
      }
    })
  },
  methods: {
    switchFilter (id, from, to) {
      this.$bus.$emit('filter-changed-' + this.context, { attribute_code: this.code, id: id, from: from, to: to })
    }
  }
}
</script>
