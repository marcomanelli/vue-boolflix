<template>
  <header>
    <div class="container">
      <h1 class="logo">Boolflix</h1>

      <div class="searchBar">
        <input v-model.trim="textToSearch" placeholder="Cerca..." type="text" />
      </div>

      <div class="header-buttons">
        <div>
        <button
          @click="$emit('startSearch', { text: textToSearch, type: 'movie' })"
        >
          CERCA FILM
        </button>
      </div>

      <div>
        <button
          @click="$emit('startSearch', { text: textToSearch, type: 'tv' })"
        >
          CERCA SERIE
        </button>
      </div>

      <div>
        <button
          @click="$emit('startSearch', { text: textToSearch, type: 'all' })"
        >
          CERCA TUTTO
        </button>
      </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Head",
  data(){
    return{
      textToSearch: ''
    }
  }
};
</script>

<style lang="scss" scoped>
header {
  background-color: rgb(32, 32, 32);
  height: 100px;
  .container {
    height: 100%;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    .logo {
      text-transform: uppercase;
      color: red;
      font-size: 50px;
    }
    .header-buttons{
      display: flex;
    }
    input {
      width: 400px;
      height: 35px;
      padding: 5px;
    }
    button {
      padding: 10px;
      border: none;
      border-radius: 5px;
      margin-right: 10px;
      transition: 0.1s;
      &:hover {
        background-color: gray;
        color: white;
      }
    }
  }
}
</style>
