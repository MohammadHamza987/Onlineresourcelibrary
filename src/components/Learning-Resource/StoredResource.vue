<template>
  <ul>
    <learning-resource
      v-for="res in resources"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
      @delete-resource="removeResource"
    >
    </learning-resource>
  </ul>
</template>

<script>
import LearningResource from "./LearningResource.vue";
export default {
    inject: ['resources', 'removeResource'],
    components: {
        LearningResource
    }
}
</script>
<style scoped>
ul {
  padding: 0;
}
</style>
