<template>
  <div class="container">
    <!-- 1. Template Syntax -->
    <div>
      <p class="title">{{ message }}</p>
      <div v-html="rawHtml"></div>
      <div :id="elementId"></div>
      <p>{{ 2 + 2 }}</p>
    </div>

    <!-- 2. Methods -->
    <div class="button-container">
      <button class="button" @click="sayHello">Click me</button>
      <button class="button" @click="methodClickHandler">Method Click</button>
    </div>

    <!-- 3. Reactivity Fundamentals -->
    <p class="title">Reactivity Fundamentals</p>
    <p>{{ reactiveValue }}</p>

    <!-- 4. Computed Properties -->
    <p class="title">Computed Properties</p>
    <p>{{ computedValue }}</p>

    <!-- 5. Class and Style Bindings -->
    <p class="title">Class and Style Bindings</p>
    <div :class="classObject"></div>
    <div :style="styleObject"></div>

    <!-- 6. List Rendering -->
    <p class="title">List Rendering</p>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item.name }}</li>
      <li v-for="n in 5" :key="n">{{ n }}</li>
      <template v-for="(item, index) in items" :key="index">
        <li>{{ item.name }}</li>
        <li v-if="item.showDetails">Toggle Details</li>
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
    <p class="title">Event Handling</p>
    <button class="button" @click="inlineClickHandler">Inline Click</button>

    <!-- 8. Form Input Bindings -->
    <p class="title">Form Input Bindings</p>
    <div class="form-container">
      <input type="text" v-model.trim="textInput" placeholder="Enter your name" />
      <input type="checkbox" v-model="checkboxValue" />
      <input type="radio" v-model="radioValue" value="option1" />
      <select v-model="selectedOption">
        <option value="option1">Option 1</option>
        <option value="option2">Option 2</option>
      </select>
      <textarea v-model.trim="textareaValue" placeholder="Enter your message"></textarea>
    </div>

    <!-- 9. Watchers -->
    <p class="title">Watchers</p>
    <p>{{ watchedValue }}</p>

    <!-- 10. Components -->
    <p class="title">Components</p>
    <MyComponent :data="items[0]" :parentValue="parentValue" @toggleDetails="toggleDetails" />

        <!-- 11. Form Input Bindings with v-model modifiers -->
    <p class="title">Form Input Bindings with Modifiers</p>
    <div class="form-container">
      <input type="text" v-model.trim="textInput" placeholder="Trimmed Input" />
      <input type="text" v-model.lazy="lazyInput" placeholder="Lazy Input" />
      <input type="number" v-model.number="numericInput" placeholder="Numeric Input" />
    </div>

    <!-- Success message -->
    <div v-if="showSuccess" class="success-message">
      <p>Form submitted successfully!</p>
    </div>
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
      lazyInput: '', // Corrected the variable name
      numericInput: null, // Corrected the variable name
      showSuccess: false, // Add a flag to track form submission success
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

/* Container styling */
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

/* Title styling */
.title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}

/* Button styling */
.button-container {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

.button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.button:hover {
  background-color: #0056b3;
}

/* Form container styling */
.form-container {
  margin-top: 20px;
}

/* Success message styling */
.success-message {
  margin-top: 20px;
  padding: 10px;
  background-color: #dff0d8;
  border: 1px solid #3c763d;
  border-radius: 4px;
  color: #3c763d;
}
</style>