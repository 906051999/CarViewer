<template>
  <div id="app">
    <h1>Car Viewer</h1>
    <div class="options">
      <!-- Options go here -->
      <button @click="toggleView">Toggle View</button>
      <button @click="highlightPart">Highlight Part</button>
    </div>
    <div class="container">
      <div class="sidebar">
        <!-- Sidebar menu goes here -->
        <ul>
          <li><a href="#">Option 1</a></li>
          <li><a href="#">Option 2</a></li>
        </ul>
      </div>
      <div id="playcanvas-container">
        <!-- PlayCanvas will be rendered here -->
      </div>
    </div>
    <div class="footer">
      <div class="color-selector">
        <!-- Color selector goes here -->
        <select>
          <option>Red</option>
          <option>Blue</option>
        </select>
      </div>
      <div class="scene-selector">
        <!-- Scene selector goes here -->
        <select>
          <option>Scene 1</option>
          <option>Scene 2</option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  methods: {
    toggleView() {
      // TODO: Implement view toggle logic
      console.log('Toggle View');
    },
    highlightPart() {
      // TODO: Implement highlight part logic
      console.log('Highlight Part');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.options {
  margin-bottom: 20px;
}

.container {
  display: flex;
}

.sidebar {
  width: 200px;
  background-color: #f0f0f0;
  padding: 20px;
}

.footer {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}
</style>
