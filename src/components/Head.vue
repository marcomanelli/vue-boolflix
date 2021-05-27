<template>
  <header>
    <div class="container">
      <div>
        <input v-model.trim="textToSearch" placeholder="Cerca..." type="text" />
      </div>

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

<style lang="scss" scoped></style>
