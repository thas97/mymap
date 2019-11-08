<template>
  <div>
    <v-row align="center" justify="center">  
        <v-img
            src="../assets/download.jpg"
            max-width="500"
            max-height="300"
        ></v-img>
    </v-row>
    <h1>My Page</h1>
    <NLink to="/about">
      <h1>About</h1>
    </NLink>
    <NLink to="/inspire">
      <h1>Inspire</h1>
    </NLink>
    <NLink to="/">
      <h1>Home</h1>
    </NLink>
  </div>
</template>
<script>
export default {
  scrollToTop: true
}
</script>
