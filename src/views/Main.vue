<template>
 <div>
    <div v-html="compiledMarkdown"></div>
  </div>
</template>
<script>
import { marked } from 'marked'

export default {
  name: 'Main',
  data () {
    return {
      context: ''
    }
  },

  created () {
    this.$http
      .get('http://localhost:8072/myservice/md/getMD/1')
      .then((res) => {
        this.context = res.data.data
      })
  },

  computed: {
    compiledMarkdown () {
      return marked(this.context, { sanitize: true })
    }
  },
  methods: {
    handleCommand (command) {
      if (command === 'cn') {
        this.$http
          .get('https://www.taiyipei.cn/myservice/md/getMD/1')
          .then((res) => {
            this.context = res.data.data
          })
      } else {
        this.$http
          .get('https://www.taiyipei.cn/myservice/md/getEnMD/1')
          .then((res) => {
            this.context = res.data.data
          })
      }
    },
    handleCommandDesc (id) {
      this.$http
        .get('https://www.taiyipei.cn/myservice/md/getMD/' + id)
        .then((res) => {
          this.context = res.data.data
        })
    }
  }
}
</script>
