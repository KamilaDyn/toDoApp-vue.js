<template>
  <header class="header">
    <h1>To-Do-List</h1>
    <div id="nav" class="container">
      <router-link class="link" to="/">Home</router-link>
      <router-link class="link" to="/about">About</router-link>
    </div>
  </header>
</template>
<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  color: white;
  text-align: center;
  text-decoration: none;
}
h1 {
  color: #1d3f77;
  text-shadow: -3px 1px 0px #74aece;
  letter-spacing: 5px;
  padding: 0.5em;
}
.container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}
.link {
  display: flex;
  text-align: center;
  text-decoration: none;
  color: #497a94;
  font-weight: bold;
  letter-spacing: 3px;
  font-size: 1.33em;
}
.link:first-child {
  border-right: 2px dotted #497a94;
  margin-right: 10px;
  padding-right: 10px;
}
</style>