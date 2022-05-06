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
      subject: {
        en: 'Welcome!',
        ko: '환영합니다!',
        ja: 'ようこそ！'
      },
      content: {
        en: 'We makes games with pleasure.',
        ko: '우리는 즐겁게 게임을 만듭니다.',
        ja: 'ゲームを楽しく作っています。'
      }
    }
  }
}
</script>
<template>
  <div class="container text-center">
    <div class="px-3 m-3 m-sm-5">
      <img src="/src/assets/furdice_logo.png" class="img-fluid rounded-start" alt="Feature Image">
      <h1>{{ subject[lang] }}</h1>
      <h4>{{ content[lang] }}</h4>
    </div>

  </div>
</template>
