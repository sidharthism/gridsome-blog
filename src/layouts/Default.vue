<template>
  <div class="layout">
    <slot/>
  </div>
</template>
<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>
<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300&family=Montserrat:wght@300&display=swap');
body{
  background-color: #f4f4f4;
  padding: 0;
  margin: 0;
}
h1,h2,h3 {
  font-family: 'Montserrat', sans-serif;
}
p{
  font-family: 'Merriweather', serif;
}
@media screen and (min-width: 992px) {
  .container {
    width: 60%;
    margin: 0 auto;
    padding: 30px 0px;
  }
}
</style>