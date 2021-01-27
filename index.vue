<template lang="pug">
  div.example-code
    Codes(v-if="!code.example" :codes="codes")
    el-card(v-else)
      div.header(slot="header")
        |{{code.title}}
      |{{code.description}}
      Codes(:codes="codes" :class="{ show: codeShow, }")
      el-divider
        i(
          :class="{ 'el-icon-arrow-down': !codeShow, 'el-icon-arrow-up': codeShow, }"
          @click="toogleCodeShow"
        )
</template>

<script>
  import isArray from 'is-array'

  import Codes from './Codes'

  export default {
    name: 'ExampleCode',
    components: { Codes, },
    props: {
      code: Array,
    },
    data () {
      return {
        codes: [],
        iconDefault: 'fas fa-laptop-code',
        codeShow: false,
      }
    },
    methods: {
      fetch () {
        const code = this.code.example || this.code

        this.codes = (isArray(code) ? code : [ code, ])
          .map(i => {
            i.content = i.content.split('\n')

            const len = i.content.length - 1

            i.content = i.content
              .filter((i, k) => {
                if (!i.trim() && (k === 0 || k === len)) return false

                return true
              })
              .join('\n')

            return i
          })
      },
      toogleCodeShow () {
        this.codeShow = !this.codeShow
      },
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

<style lang="scss" scoped>
  .example-code {
    width: 100%;
  }
</style>

<style lang="scss" scoped>
  .example-code {
    .el-card {
      padding-bottom: 0;

      .header {
        line-height: 0;
        font-weight: bold;
      }

      .el-tabs {
        transition: all 2s 0s;
        max-height: 0;
        opacity: 0;
        overflow: hidden;
        margin-top: 1rem;

        &.show {
          max-height: 500px;
          opacity: 1;
        }
      }
    }
  }
</style>