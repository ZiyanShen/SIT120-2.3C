<template>
  <div>
    <!-- 1. Template Syntax -->
    <p>{{ message }}</p>
    <p v-html="rawHtml"></p>
    <div :id="inputId"></div>
    <p>{{ message + ' from Vue!' }}</p>

    <!-- 2. Methods -->
    <button @click="sayHello">Say Hello</button>

    <!-- 3. Reactivity Fundamentals -->
    <p>{{ count }}</p>
    <button @click="increment">Increment</button>

    <!-- 4. Computed Properties -->
    <p>{{ doubledValue }}</p>

    <!-- 5. Class and Style Bindings -->
    <div :class="{ active: isActive }">Active Class</div>
    <div :style="{ color: textColor }">Colored Text</div>

    <!-- 6. List Rendering -->
    <ul>
      <li v-for="(value, key) in items" :key="key">{{ key }}: {{ value }}</li>
    </ul>

    <!-- 7. Event Handling -->
    <button @click="handleClick">Inline Event</button>

    <!-- 8. Form Input Bindings -->
    <input type="text" v-model="textInput" />
    <input type="checkbox" v-model="isChecked" />
    <input type="radio" v-model="selectedOption" value="option1" />
    <input type="radio" v-model="selectedOption" value="option2" />
    <select v-model="selectedItem">
      <option value="item1">Item 1</option>
      <option value="item2">Item 2</option>
    </select>
    <textarea v-model="textareaInput"></textarea>

    <!-- 9. Watchers -->
    <input type="text" v-model="valueToWatch">

    <!-- 10. Components -->
    <child-component :message="parentMessage" @message-sent="handleMessage"></child-component>
    <p>{{ receivedMessage }}</p>

  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue'; // Import your child component

export default {
  components: {
    'child-component': ChildComponent,
  },
  data() {
    return {
      // 1. Template Syntax
      message: 'Hello, Vue!',
      rawHtml: '<span style="color: red;">Raw HTML content</span>',
      inputId: 'unique-id',

      // 2. Methods

      // 3. Reactivity Fundamentals
      count: 0,

      // 4. Computed Properties

      // 5. Class and Style Bindings
      isActive: true,
      textColor: 'blue',

      // 6. List Rendering
      items: { name: 'John', age: 30, country: 'USA' },

      // 7. Event Handling

      // 8. Form Input Bindings
      textInput: '',
      isChecked: false,
      selectedOption: '',
      selectedItem: '',
      textareaInput: '',

      // 9. Watchers
      valueToWatch: '',

      // 10. Components
      parentMessage: 'Hello from parent!',
      receivedMessage: '',
    };
  },
  methods: {
    // 2. Methods
    sayHello() {
      alert('Hello, Vue!');
    },
    // 3. Reactivity Fundamentals
    increment() {
      this.count++;
    },
    // 7. Event Handling
    handleClick() {
      alert('Inline event handler clicked');
    },
    handleMessage(message) {
      this.receivedMessage = message;
    },
  },
  computed: {
    // 4. Computed Properties
    doubledValue() {
      return this.count * 2;
    },
  },
  watch: {
    // 9. Watchers
    valueToWatch(newValue, oldValue) {
      console.log(newValue,oldValue);
      // Watcher logic goes here (not included in this example)
    },
  },
  // 10. Components
  // 11. Router
  // Vue Router setup goes here (not included in this example)
};
</script>
