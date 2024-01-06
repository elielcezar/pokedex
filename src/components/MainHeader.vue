<template>
  <header>
    <div class="container">
      <h1><img src="../assets/img/logo-pokedex.svg" /></h1>
      <nav>
        <router-link to="/">Home</router-link>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'MainHeader'
}
</script>

<style lang="scss" scoped>
//@import url('@/assets/styles/_global.scss');

h1{
  width: 100%;
  text-align: center;
  margin: 25px 0;  

  img{        
    display: inline-block;

    @media(min-width: 768px){
      max-width: 400px;
    }
  }
}

nav{
  width: 100%;
  border-radius: 50px;
  padding: 10px;
  margin-bottom: 40px;
  background: var(--bright-blue);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 10px var(--light-blue);

  a{
    color: var(--dark-blue);
    font-size: 1.5rem;
    font-weight: 500;
  }
}

</style>