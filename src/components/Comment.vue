<template>
  <div class="comment">
    <article class="comment-body markdown-body" v-html="renderedMarkdown"/>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        renderedMarkdown: ''
      }
    },
    props: ['comment'],
    methods: {
      renderMarkdown () {
        this.renderedMarkdown = ''
        if (this.comment.body_html) {
          this.renderedMarkdown = this.comment.body_html
        } else if (this.comment.body) {
          this.renderedMarkdown = this.$marked(this.comment.body)
        }
      }
    },
    mounted () {
      this.$nextTick(() => {
        this.renderMarkdown()
      })
    }
  }
</script>
