<template lang="pug">
  div.example-code
    el-tabs(type="border-card")
      el-tab-pane(
        v-for="(Code, k) in codes" :key="k"
        :label="Code.name ? `${Code.name} (${Code.lang})` : Code.lang"
      )
        pre(v-html="Code.content")
</template>

<script>
  import isArray from 'is-array'

  export default {
    name: 'ExampleCode',
    props: {
      code: Array,
    },
    data () {
      return {
        codes: [],  
      }
    },
    methods: {
      fetch () {
        this.codes = (isArray(this.code) ? this.code : [ this.code, ])
          .map(i => {
            i.content = i.content
              .split('<').join('&lt;')
              .split('>').join('&gt;')

            i.content = i.content.split('\n')

            const len = i.content.length - 1

            i.content = i.content
              .filter((i, k) => {
                if (!i.trim() && (k === 0 || k === len)) return false

                return true
              })
              .join('<br />')

            return i
          })
      }
    },
    mounted () {
      this.fetch()
    },
    watch: {
      defs: {
        deep: true,
        handler () {
          this.fetch()
        },
      },
    },
  }
</script>

<style lang="scss">
  .example-code {
    width: 100%;
  }
</style>