<template>
  <div class="container">
    <left-layout class="left-container"/>
    <div class="about-me bga-back-top">
      <article class="markdown-body" v-html="renderedMarkdown"/>
    </div>
  </div>
</template>
<style lang="scss" scoped>
  .about-me {
    flex-grow: 1;
    padding: 30px;
    overflow-y: auto;
  }
</style>
<script>
  import LeftLayout from '../components/LeftLayout.vue'
  export default {
    data () {
      return {
        renderedMarkdown: ''
      }
    },
    components: {
      LeftLayout
    },
    methods: {
      getReadme () {
        this.$gitHubApi.getReadme(this).then(response => {
          if (response.data) {
            this.renderedMarkdown = this.$marked(response.data)
          }
        })
      }
    },
    mounted () {
      this.$nextTick(() => {
        this.getReadme()
      })
    }
  }
</script>
