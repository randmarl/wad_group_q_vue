<template>
  <div id="app">
    <nav>
      <router-link to="/" class="nav-button">Home</router-link>
      <router-link to="/login" class="nav-button">Login</router-link>
    </nav>
    <main>
      <router-view/>
    </main>
    <footer>
      <p>&copy; Marleen Rand, Anna-Liisa Jõgi, Kim Lilii Tamm. PostIt, 2024. All rights reserved.</p>
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
  height: 100vh;
  justify-content: center;
  align-items: stretch;
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  margin: 0;
	padding: 0;
}

body, html {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

nav {
  background-color: #333;
	flex-direction: row;
	justify-content: space-evenly;
	display: flex;
	align-items: center;
  color: white;
  padding: 10px 0;
  gap: 10px;
}

.nav-button {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  text-decoration: none;
  border-radius: 5px;
  font-weight: bold;
  border: 1px solid #007bff;
  transition: 0.3s;
}

.nav-button:hover {
  background-color: white;
  color: #007bff;
  border: 1px solid #007bff;
}

main {
  flex: 1;
  overflow-y: auto;
  padding: 20px;
}

footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 10px 0;
  position: fixed;
  bottom: 0;
  width: 100%;
 }
</style>
