<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
      <img id="logo" :src="logo" :alt="alt" />
    </router-link>
    <router-link to="/">Home</router-link> |
    <router-link to="/pedidos">Pedidos</router-link>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  props: ['logo', 'alt'],
}
</script>

<style>
#nav {
  background-color: #222;
  border-bottom: 1px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav #logo-url {
  margin: auto;
  margin-left: 0;
}
#logo {
  height: 40px;
  margin: 0 15px;
}
#nav a#logo-url {
  border-bottom: none;
}
#nav a {
  color: #fefefe;
  text-decoration: none;
  margin: 0 15px;
  transition: 0.5s;
}
#nav a:hover {
  color: #fff;
  border-bottom: 1px solid #fefefe;
}
</style>
