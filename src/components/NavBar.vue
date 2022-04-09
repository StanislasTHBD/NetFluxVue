<template>
    <div>
        <h1>Netflux</h1>
        <button class="button centernav">Ma Liste</button>
        <button class="button centernav">Films</button>
        <button class="button centernav">Séries</button>
        <button class="button centernav">A propos</button>
    </div>
    <div>
        <h2>Films</h2>
    </div>
</template>

<style scoped>
@import url('http://fonts.cdnfonts.com/css/gotham');
h1{
    font-family: 'Gotham Thin', sans-serif;
    color:red;
    text-align: center;
    font-size: 80px;
}
h2{
    color: red;
    text-align: center;
    font-size: 30px;
}
.button {
    background-color: grey;
    border-collapse: collapse;
    color: red;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 20px;
    text-align: center;
}
.centernav {
  margin-left: auto;
  margin-right: auto;
  width: 400px;
}
</style>