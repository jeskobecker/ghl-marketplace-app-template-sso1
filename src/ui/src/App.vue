<template>
  <div class="app-container">
    <h1>Location Dashboard</h1>
    <div v-if="userData" class="user-info">
      <h2>Welcome, {{ userData.name }}</h2>
      <p>Location: {{ userData.locationName }}</p>
      <p>Company: {{ userData.companyName }}</p>
    </div>
    <div v-else>
      Loading user data...
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      userData: null
    }
  },
  async mounted(){
    const data = await window.ghl.getUserData();
    this.userData = data;
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.app-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.user-info {
  background: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
  margin-top: 20px;
}

h1 {
  color: #42b983;
  margin-bottom: 30px;
}
</style>
