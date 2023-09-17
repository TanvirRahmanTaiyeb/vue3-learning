<template>
  <div>
    <h2>{{ data.name }}</h2>
    <button @click="showDetails">Toggle Details</button>
    <p>Parent Value: {{ parentValue }}</p>
  </div>
</template>

<script>
export default {
  props: {
    data: Object,
    parentValue: String,
  },
  methods: {
    showDetails() {
      this.$emit('toggleDetails', this.data.id);
    },
  },
};
</script>

<style scoped>
/* component's style code here */
</style>
