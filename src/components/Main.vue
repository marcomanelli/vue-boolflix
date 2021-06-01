<template>
  <main class="container">
    <h1>{{ titles[type] }}</h1>
    <div class="card-box">
      <Card
      class="object-card"
      v-for="card in list"
      :key="card.id"
      :card="card"
    />
    </div>
  </main>
</template>

<script>
import Card from '@/components/Card';

export default {
  name: 'Main',
  components:{
    Card
  },
  props:{
    type: String,
    list: Array
  },
  data(){
    return{
      titles:{
        'movie': 'Film trovati',
        'tv': 'Serie tv trovate'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  h1 {
    text-align: center;
    padding-top: 30px;
    text-transform: uppercase;
  }
  background-color: rgb(99, 99, 99);
  width: 100%;
  height: 100%;
  .card-box {
    display: flex;
    flex-wrap: wrap;
    margin: 0 10px;
  }
  .object-card {
    margin-top: 30px;
  }
}
</style>