<template>
  <div>
    <h2>{{ data.name }}</h2>
    <button @click="showDetails">Toggle Details</button>
    <p>Parent Value: {{ parentValue }}</p>
    <slot></slot> <!-- Add a slot -->
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
/* Your component's style code here */
</style>
