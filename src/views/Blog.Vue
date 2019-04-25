<template>
  <div class="container">
    <left-layout class="left-container"/>
    <div class="blog-container main-container">
      <labels-list/>
      <router-view/>
    </div>
  </div>
</template>
<script>
  import LeftLayout from '../components/LeftLayout.vue'
  import LabelsList from '../components/LabelsList.vue'

  export default {
    components: {
      LeftLayout, LabelsList
    }
  }
</script>
