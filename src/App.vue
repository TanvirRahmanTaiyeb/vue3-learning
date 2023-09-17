<template>
  <div id="app">
    <!-- Include the DemoComponent -->
    <DemoComponent />

    <!-- Add the input field with 'v-model' modifiers -->
    <input type="text" id="username" v-model.lazy="username" />

    <!-- Add content for Option 2 -->
    <div v-if="selectedOption === 'option2'">
      <!-- content for Option 2 goes here -->
      <p>This is content for Option 2.</p>
    </div>
    
    <!-- Use router-view to display routed components -->
    <router-view></router-view>
  </div>
</template>

<script>
import DemoComponent from './components/DemoComponent.vue';

export default {
  name: 'App',
  components: {
    DemoComponent,
  },
  data() {
    return {
      username: '', // This is where I can store the input value
      selectedOption: 'option1', // Default option
    };
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
