<template lang="pug">
  div.example-code
    el-tabs(type="border-card")
      el-tab-pane(v-for="(Code, k) in codes" :key="k")
        span(slot="label")
          i(:class="getTabIcon(Code)")
          | {{getTabName(Code, k + 1)}}
        pre(v-html="getCodeContent(Code)")
</template>

<script>
  import isArray from 'is-array'
  import Syntax from "syntax"

  export default {
    name: 'ExampleCode',
    props: {
      code: Array,
    },
    data () {
      return {
        codes: [],
        iconDefault: 'fas fa-laptop-code',
      }
    },
    methods: {
      getCodeContent (Code) {
        try {
          let syntax = new Syntax({ language: this.getValidSyntaxLang(Code), })
  
          return syntax.richtext(Code.content).html()
        }
        catch (e) {
          return Code.content
        }
      },
      getValidSyntaxLang (Code) {
        switch (Code.lang.toLowerCase()) {
          case 'javascript':
          case 'js': return 'js'
          case 'ts':
          case 'typescript': return 'typescript'
          case 'html': 
          case 'pug': 
          case 'jade': return 'xml'
          case 'css': 
          case 'sass':
          case 'scss': return 'css'
          case 'less':
          case 'lesscss': return 'less'
          case 'bash': 
          case 'prompt':
          case 'cmd': 
          case 'terminal': return 'bash'
          // case 'env': return 'ini'
          // case 'db': 
          // case 'database':
          // case 'sql': return 'bash'
          default: return 'bash'
        }
      },
      getTabIcon (Code) {
        switch (Code.lang.toLowerCase()) {
          case 'js':
          case 'ts':
          case 'javascript':
          case 'typescript': return 'fab fa-js'
          case 'html':
          case 'pug': 
          case 'jade': return 'fas fa-code'
          case 'css': return 'fab fa-css3'
          case 'sass':
          case 'scss': return 'fab fa-sass'
          case 'less':
          case 'lesscss': return 'fab fa-less'
          case 'bash':
          case 'prompt':
          case 'cmd': 
          case 'terminal': return 'fas fa-terminal'
          case 'env': return 'fas fa-list'
          case 'db':
          case 'database':
          case 'sql': return 'fas fa-database'
          default: return this.iconDefault
        }
      },
      getCodeLang (Code) {
        switch (Code.lang.toLowerCase()) {
          case 'javascript':
          case 'js': return 'JavaScript'
          case 'ts':
          case 'typescript': return 'TypeScript'
          case 'html': return 'HTML'
          case 'pug': return 'PUG'
          case 'jade': return 'JADE'
          case 'css': return 'CSS'
          case 'sass':
          case 'scss': return 'SASS'
          case 'less':
          case 'lesscss': return 'LESS'
          case 'bash': return 'Bash'
          case 'prompt': return 'Prompt'
          case 'cmd': return 'Cmd'
          case 'terminal': return 'Terminal'
          case 'env': return 'ENV'
          case 'db': return 'DB'
          case 'database': return 'DataBase'
          case 'sql': return 'SQL'
          default: return undefined
        }
      },
      getTabName (Code, k) {
        const name = Code.name
        const lang = this.getCodeLang(Code)
        const nameExists = name !== undefined
        const langExists = lang !== undefined

        if (!nameExists && langExists) {
          return lang
        }

        if (nameExists && !langExists) {
          return `${name} (${Code.lang})`
        }

        if (nameExists) {
          return name
        }

        return `Tab ${k} (${Code.lang})`
      },
      fetch () {
        this.codes = (isArray(this.code) ? this.code : [ this.code, ])
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

    i,
    svg,
    svg path {
      margin-right: 5px;
    }
  }
</style>