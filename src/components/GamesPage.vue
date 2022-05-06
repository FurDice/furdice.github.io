<script setup>
defineProps({
  lang: {
    type: String,
    required: true
  }
})
</script>
<script>
import egg_feature_img from '@/assets/egg_feature.png'
// import sample_img from '@/assets/sample.png'

export default {
  data() {
    return {
      games: [
        {
          img: egg_feature_img,
          title: {
            en: 'There Were Eggs',
            ko: 'R이있었다',
            ja: 'たまごがいた'
          },
          description: {
            en: 'Merge eggs to discover new cute characters. The most adorable 2048 Merge Game',
            ko: '알과 캐릭터를 합쳐 점점 새로운 모습을 발견해 나가는 귀여운 2048 합치기 게임',
            ja: '卵とキャラクターを合わせてますます新しい姿を発見していく可愛い2048合わせゲーム'
          },
          releaseDate: {
            en: 'Released on May 2022',
            ko: '출시일: 2022년 5월',
            ja: 'リリース日: 2022年 5月 '
          },
          google: 'https://play.google.com/store/apps/details?id=games.furdice.egg',
          apple: null
        },
      ]
    }
  }
}
</script>
<template>
  <div class="container">
    <!-- There Were Eggs -->
    <div class="card mb-3 my-3" v-for="game in games">
      <div class="row g-0">
        <div class="col-md-4">
          <img :src="game.img" class="img-fluid rounded-start" alt="Feature Image">
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ game.title[lang] }}</h5>
            <p class="card-text">{{ game.description[lang] }}</p>
            <p class="card-text"><small class="text-muted">{{ game.releaseDate[lang] }}</small></p>
            <a :href="game.google" class="btn btn-primary">
              <i class="bi bi-google"></i> Play Store
            </a>
          </div>
        </div>
      </div>
    </div>
    <!-- To the Star -->
  </div>
</template>
