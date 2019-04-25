<template>
  <div class="app">
    <router-view />
    <bga-back-top :svgMajorColor="'#7b79e5'" :bottom="90" :right="5" :svgMinorColor="'#ba6fda'" :svgType="'rocket_smoke'"/>
  </div>
</template>
<script>
  import { mapActions } from 'vuex'

  export default {
    methods: {
      ...mapActions([
        'setLabels',
        'setGitHubUser'
      ])
    },
    mounted () {
      this.$nextTick(function () {
        this.$gitHubApi.getUserInfo(this).then(this.$http.spread((userResp, labelResp) => {
          this.setGitHubUser(userResp.data)
          this.setLabels(labelResp.data)
        }))
      })
    }
  }
</script>
