<template>
  <div>
    <!-- 1. Template Syntax -->
    <div>
      <p>{{ message }}</p>
      <div v-html="rawHtml"></div>
      <div :id="elementId"></div>
      <p>{{ 2 + 2 }}</p>
    </div>

    <!-- 2. Methods -->
    <button @click="sayHello">Click me</button>

    <!-- 3. Reactivity Fundamentals -->
    <p>{{ reactiveValue }}</p>

    <!-- 4. Computed Properties -->
    <p>{{ computedValue }}</p>

    <!-- 5. Class and Style Bindings -->
    <div :class="classObject"></div>
    <div :style="styleObject"></div>

    <!-- 6. List Rendering -->
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item.name }}</li>
      <li v-for="n in 5" :key="n">{{ n }}</li>
      <template v-for="(item, index) in items" :key="index">
        <li>{{ item.name }}</li>
        <li v-if="item.showDetails">Details</li>
      </template>
      <MyComponent
        v-for="(item, index) in items"
        :key="index"
        :data="item"
        @toggleDetails="toggleDetails"
        :parentValue="parentValue"
      />
    </ul>

    <!-- 7. Event Handling -->
    <button @click="inlineClickHandler">Inline Click</button>
    <button @click="methodClickHandler">Method Click</button>

    <!-- 8. Form Input Bindings -->
    <input type="text" v-model="textInput" />
    <input type="checkbox" v-model="checkboxValue" />
    <input type="radio" v-model="radioValue" value="option1" />
    <select v-model="selectedOption">
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
    </select>
    <textarea v-model="textareaValue"></textarea>

    <!-- 9. Watchers -->
    <p>{{ watchedValue }}</p>

    <!-- 10. Components -->
    <MyComponent :data="items[0]" :parentValue="parentValue" @toggleDetails="toggleDetails" />
  </div>
</template>

<script>
import MyComponent from './MyComponent.vue';
import { ref, computed } from 'vue';

export default {
  data() {
    return {
      message: "Hello, Vue!",
      rawHtml: "<span>Raw HTML</span>",
      elementId: "myElement",
      reactiveValue: ref(0),
      items: [
        { id: 1, name: "Item 1", showDetails: true },
        { id: 2, name: "Item 2", showDetails: false },
      ],
      computedValue: computed(() => this.items.length),
      classObject: { active: true, "text-success": true },
      styleObject: { color: "red", fontSize: "20px" },
      textInput: "",
      checkboxValue: false,
      radioValue: "",
      selectedOption: "option1",
      textareaValue: "",
      watchedValue: "",
      parentValue: "Parent Value",
    };
  },

  methods: {
    sayHello() {
      alert("Hello from Vue!");
    },

    inlineClickHandler() {
      alert("Inline click handler");
    },
    methodClickHandler() {
      alert("Method click handler");
    },

    toggleDetails(itemId) {
      this.items = this.items.map(item => {
        if (item.id === itemId) {
          item.showDetails = !item.showDetails;
        }
        return item;
      });
    },
  },

  components: {
    MyComponent,
  },
};
</script>

<style scoped>
/* Component's style code here */
.active {
  font-weight: bold;
}

.text-success {
  color: green;
}
</style>

<style>
/* External CSS */
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

/* Style the app container */
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 40px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
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
</style>
