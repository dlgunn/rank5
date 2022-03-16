<template>
  <nav>
    <h1>Top5</h1>
    <div class="elements">
      <router-link to="/"><h4>Home</h4> </router-link> |
      <router-link to="/about"><h4>About</h4></router-link>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style scoped>
nav {
  padding: 30px;
  border-bottom-style: solid;
  border-color: #2c3e50a1;
  border-width: 1px;
  display: flex;
  justify-content: space-between;
  background-color: rgba(141, 141, 238, 0.281);
}

nav h4 {
  margin-top: 0px;
  margin-bottom: 0px;
  margin-left: 3px;
  margin-right: 3px;
}

.elements {
  display: flex;
  align-items: center;
}

nav h1 {
  margin: 0px;
  padding: 0px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

nav a:hover {
  text-decoration: underline;
}

nav a.router-link-exact-active {
  color: #4258b9;
}
</style>
