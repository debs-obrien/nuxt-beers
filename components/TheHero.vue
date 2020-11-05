<template>
  <section class="masthead" role="img" aria-label="Image Description">
    <h1>Welcome to Nuxt Beers</h1>
    <NuxtLink to="/beers" class="link">Let's start drinking</NuxtLink>
  </section>
</template>

<script>
export default {}
</script>

<style scoped>
.masthead {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
  width: 100%;
  height: 70vh; /* if you don't want it to take up the full screen, reduce this number */
  overflow: hidden;
  background: linear-gradient(
      to top,
      rgba(0, 0, 0, 0) 0%,
      rgba(0, 0, 0, 0) 37%,
      rgba(0, 0, 0, 0.65) 100%
    ),
    url('~assets/beer.jpg') no-repeat center center scroll;
  background-size: cover !important;
}

h1 {
  font-style: normal;
  font-weight: bold;
  color: #eee;
  font-size: 11vmin;
  letter-spacing: 0.03em;
  line-height: 1;
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.8);
  margin-bottom: 84px;
}

.link {
  background: #900951;
  transition: background ease 0.25s;
  border-radius: 9px;
  display: inline-block;
  border: none;
  padding: 0.75rem 1.5rem;
  margin: 0;
  text-decoration: none;
  color: #fff;
  font-size: 1.2rem;
  cursor: pointer;
  text-align: center;
  -webkit-appearance: none;
  -moz-appearance: none;
}
button:hover {
  background: #b76273;
}
button:focus {
  outline: 1px solid #fff;
  outline-offset: -4px;
}
</style>
