<template>
  <div id="app">
    <DemoComponent />
    <input type="text" id="username" v-model="username" />
    <div v-if="selectedOption === 'option2'">
      <p>This is content for Option 2.</p>
    </div>
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
      username: '',
      selectedOption: 'option1',
    };
  },
};
</script>

<style>
/* Existing styles for #app */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

/* custom styles from styles.css */
/* Reset default margin and padding on all elements */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Apply a background color to the entire app */
body {
  background-color: #f0f0f0;
}

/* Style the input field */
#username {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
}

/* Style the router view content */
.router-view-content {
  padding: 20px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}

/* Add more custom styles as needed */
</style>
