<template>
  <div class="p-3">
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img
            :src="imageURL + card.poster_path"
            :alt="card.title || card.name"
          />
        </div>
        <div class="flip-card-back">
          <p>
            <strong>Titolo: </strong>
            {{ card.title || card.name }}
          </p>
          <p>
            <strong>Titolo originale: </strong>
            {{ card.original_title || card.original_name }}
          </p>

          <p>
            <strong>Lingua: </strong>
            <img
              class="flag"
              v-if="flags.includes(card.original_language)"
              :src="require(`@/assets/img/${card.original_language}.png`)"
              :alt="card.original_language"
            />
            <span v-else>{{ card.original_language }}</span>
          </p>
          <p>
            <strong>Trama: </strong>
            {{ card.overview }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: Object,
  },
  data(){
    return{
      flags:['it','en'],
      imageURL: 'https://image.tmdb.org/t/p/w342'
    }
  },
};
</script>

<style lang="scss" scoped>
  .flag{
    width: 30px;
  }
  .flip-card {
  background-color: transparent;
  width: 342px;
  height: 513px;
  perspective: 1000px;
}
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  font-size: 0.75rem;
}
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  background-color: #202020;
  border: 1px solid white;
  
}
.flip-card-front {
  color: black;
  img{
    width: 100%;
  }
}
.flip-card-back {
  color: white;
  transform: rotateY(180deg);
  padding:10px;
}
</style>
