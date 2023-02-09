<template>
  <ol class="list">
      <li v-for="(movie, i) in movies" :key="movie.name">
        <a href="">
          <h4 class="hide">{{ movie.name }}</h4>
          <span class="hide rate" :class='"rate" + movie.rate[0]'>{{ movie.rate[1] }}</span>
          <strong class="rank">{{ i + 1 }}</strong>
          <img class="poster" :src="require(`@/assets/${movie.src}`)" :alt="movie.name" />
          <!-- score -->
          <span class="desc" v-if="movContext === '평점순'">
            <i class="star"><b :style="{ width: movie.score * 10 + '%' }"></b></i>
            <em class="score">{{ movie.score }}</em>
          </span>
          <!-- ticketing -->
          <span class="desc" v-else-if="movContext === '예매순'">
            <i class="reserv title">예매율</i>
            <em class="reserv data">{{ movie.ticketing }}%</em>
          </span>
          <!-- opendate -->
          <span class="desc" v-else-if="movContext === '개봉일순'">
            <em class="opendate">{{ movie.openDate }} <b>개봉</b></em>
          </span>
          <!-- week -->
          <span class="desc" v-else-if="movContext === '주말관객순'">
            <i class="week title">주말 관객</i>
            <em class="week data">{{ movie.week }} 명</em>
          </span>
          <!-- sale -->
          <span class="desc" v-else-if="movContext === '다운로드순'">
            <i class="sale title">판매율</i>
            <em class="sale data">{{ movie.sale }} %</em>
          </span>
        </a>
      </li>
    </ol>
</template>

<script>
export default {
    props: {
        movies: Array,
        movContext: String,
    },
}
</script>

<style>

</style>