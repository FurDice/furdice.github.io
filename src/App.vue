<script setup>
import HomePage from './components/HomePage.vue';
import GamesPage from './components/GamesPage.vue';
import PrivacyPage from './components/PrivacyPage.vue';
</script>

<script>
export default {
  data() {
    return {
      tab: 'home', // home, games, privacy
      lang: 'en', // ko en ja zh
      langs: {
        ko: '한국어',
        en: 'English',
        ja: '日本語'
      }
    }
  },
  created() {
    // 1. Set Page
    const urlParams = new URLSearchParams(window.location.search);
    if (urlParams.has('page')) {
      const page = urlParams.get('page')
      switch (page) {
        case 'home': this.tab = 'home'; break;
        case 'games': this.tab = 'games'; break;
        case 'privacy': this.tab = 'privacy'; break;
      }
    }

    // 2. Set Default Language
    const browserLanguage = navigator.language
    for (const code in this.langs) {
      if (browserLanguage.startsWith(code)) {
        this.lang = code
        return
      }
    }
  }
}
</script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container">
        <a class="navbar-brand" href="#">
          <img alt="FurDice logo" class="logo" src="@/assets/furdice_outline_900x900.png" width="64" height="64"/>
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#toggler"
                aria-controls="toggler" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="toggler">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link" :class="{ active: tab=='home'}" aria-current="page" @click="tab='home'">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" :class="{ active: tab=='games'}" aria-current="page" @click="tab='games'">Games</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" :class="{ active: tab=='privacy'}" @click="tab='privacy'">Privacy Policy</a>
            </li>
          </ul>
          <div class="dropdown">
            <button class="btn btn-secondary-outline dropdown-toggle" type="button" id="dropdownMenu2"
                    data-bs-toggle="dropdown" aria-expanded="false">
              {{ langs[lang] }}
            </button>
            <ul class="dropdown-menu" aria-labelledby="dropdownMenu2">
              <li>
                <button class="dropdown-item" type="button" @click="lang='en'">English</button>
              </li>
              <li>
                <button class="dropdown-item" type="button" @click="lang='ko'">한국어</button>
              </li>
              <li>
                <button class="dropdown-item" type="button" @click="lang='ja'">日本語</button>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </nav>
  </header>

  <main>
    <HomePage v-show="tab=='home'" :lang="lang"/>
    <GamesPage v-show="tab=='games'" :lang="lang"/>
    <PrivacyPage v-show="tab=='privacy'" :lang="lang"/>
  </main>
</template>

<style>
/*@import './assets/base.css';*/

/*#app {*/
/*  max-width: 1280px;*/
/*  margin: 0 auto;*/
/*  padding: 2rem;*/

/*  font-weight: normal;*/
/*}*/

/*header {*/
/*  line-height: 1.5;*/
/*}*/

/*.logo {*/
/*  display: block;*/
/*  margin: 0 auto 2rem;*/
/*}*/

/*a,*/
/*.green {*/
/*  text-decoration: none;*/
/*  color: hsla(160, 100%, 37%, 1);*/
/*  transition: 0.4s;*/
/*}*/

/*@media (hover: hover) {*/
/*  a:hover {*/
/*    background-color: hsla(160, 100%, 37%, 0.2);*/
/*  }*/
/*}*/

/*@media (min-width: 1024px) {*/
/*  body {*/
/*    display: flex;*/
/*    place-items: center;*/
/*  }*/

/*  #app {*/
/*    display: grid;*/
/*    grid-template-columns: 1fr 1fr;*/
/*    padding: 0 2rem;*/
/*  }*/

/*  header {*/
/*    display: flex;*/
/*    place-items: center;*/
/*    padding-right: calc(var(--section-gap) / 2);*/
/*  }*/

/*  header .wrapper {*/
/*    display: flex;*/
/*    place-items: flex-start;*/
/*    flex-wrap: wrap;*/
/*  }*/

/*  .logo {*/
/*    margin: 0 2rem 0 0;*/
/*  }*/
/*}*/
</style>
