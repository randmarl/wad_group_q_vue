<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/login">Login</router-link>
    </nav>
    <main>
      <router-view/>
    </main>
    <footer>
      <p> Copyright text things and else </p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  margin: 0;
	padding: 0;
}
nav {
  flex: 0 0 60px;
  padding: 30px;
  background-color: #333;
	flex-direction: row;
	justify-content: space-between;
	display: flex;
	align-items: center;
  color: white;
}

nav a {
  font-weight: bold;
	color: white;
}

nav a.router-link-exact-active {
  color: #42b983;
}
main {
  flex: 1;
  overflow-y: auto;
  padding: 20px;
}

footer {
  flex: 0 0 40px;
  padding: 30px;
  background-color: #333;
	flex-direction: row;
  color: white;
}
</style>
