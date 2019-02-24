<template>
  <v-app>
    <v-toolbar app class="white--text" :class="isAtTop && isHome() ? 'transparent' : 'deepblue'" dense>
      <v-toolbar-title class="headline text-uppercase logo-name" @click="onHomeClick()">
        <v-icon color="red" style="background-color: pink">favorite</v-icon>
        <span class="font-weight-light" style="margin-left: 20px">AFROPICS</span>
      </v-toolbar-title>
      <span style="width: 30px"></span>
      <v-form @submit.native="onSearchClick()">
        <v-text-field
                v-if="!(isAtTop && isHome())"
                class="compact"
                background-color="white"
                v-model="search"
                placeholder="Chercher des photos"
                append-icon="search"
                @click:append="onSearchClick()"
                solo
                required
        ></v-text-field>
      </v-form>
      <v-spacer></v-spacer>
      <v-btn
              flat
              color="white"
              @click="onAboutClick()"
      >
        <span class="mr-2">Explorer</span>
      </v-btn>
      <v-btn
              flat
              color="white"
              @click="onAboutClick()"
      >
        <span class="mr-2">Licence</span>
      </v-btn>
      <v-btn
              flat
              color="white"
              @click="onAboutClick()"
      >
        <span class="mr-2"><v-icon>more_horiz</v-icon></span>
      </v-btn>
      <v-btn
              dark
              color="#05a081"
              @click="onAboutClick()"
      >
        <span class="mr-2">Inscription</span>
      </v-btn>
    </v-toolbar>

    <div class="hero" v-if="isHome()">
      <div class="hero-image">
        <img src="https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=350.0&amp;w=1400" srcset="https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=250.0&amp;w=1000 1000w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=375.0&amp;w=1500 1500w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=500.0&amp;w=2000 2000w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=625.0&amp;w=2500 2500w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=750.0&amp;w=3000 3000w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=875.0&amp;w=3500 3500w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=1000.0&amp;w=4000 4000w,https://images.pexels.com/photos/1674817/pexels-photo-1674817.jpeg?auto=compress&amp;cs=tinysrgb&amp;fit=crop&amp;h=1250.0&amp;w=5000 5000w">
      </div>
      <div class="hero-content">
        <div class="hero-title">Les meilleurs free stock photos partagées par des photographes talentueux.</div>
        <v-form @submit.native="onSearchClick()">
          <v-text-field
                  background-color="white"
                  v-model="search"
                  placeholder="Chercher des photos"
                  append-icon="search"
                  @click:append="onSearchClick()"
                  solo
                  autofocus
                  required
          ></v-text-field>
        </v-form>
      </div>
    </div>

    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<style>
  .logo-name {
    cursor: pointer;
  }
  .deepblue {
    background-color: #232a34 !important;
    border-color: #232a34 !important;
  }
  .compact {
    transform: scale(0.7);
    transform-origin: left;
  }
  .hero {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 16px;
    padding-top: 66px;
    padding-bottom: 66px;
    color: #fff;
    background-color: #ccc;
    height: 100%;
    max-height: 500px;
    z-index: 0;
    padding-top: 130px;
  }
  .hero:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(180deg,rgba(34,34,34,0.6) 0%,rgba(34,34,34,0.1) 100%);
    z-index: 1;
  }
  .hero-image {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  .hero-image img {
    width: 100%;
    height: 100%;
    -o-object-fit: cover;
    object-fit: cover;
    background: #232a34;
  }

  .hero-content {
    max-width: 650px;
    width: 100%;
    z-index: 2;
    height: 260px;
  }
  .hero-title {
    display: block;
    font-size: 32px;
    line-height: 42px;
    letter-spacing: -.8px;
    margin-top: 0;
    margin-bottom: 21px;
    font-weight: 400;
    font-weight: 700;
  }
</style>

<script>
    export default {
        data: () => ({
            search: '',
            isAtTop: true,
        }),
        mounted() {
            window.addEventListener('scroll', this.handleScroll);
        },
        computed: {
        },
        methods: {
            isHome() {
                return this.$router.currentRoute.name === 'home'
            },
            onHomeClick() {
                this.$router.push({name: 'home'})
            },
            onAboutClick() {
                this.$router.push({name: 'about'})
            },
            handleScroll() {
                this.isAtTop = window.scrollY < 100
            },
            onSearchClick() {
                this.$router.push({name: 'about'})
                this.search = ''
            }
        }
    }

</script>