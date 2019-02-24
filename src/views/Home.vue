<template>
  <v-container fluid>
    <v-toolbar flat>
      <label>Free stock photos</label>
      <v-btn @click="onAboutClick">Tendances</v-btn>
      <v-btn @click="onAboutClick">Nouveautés</v-btn>
    </v-toolbar>

    <div class="image-list">
      <image-block :item="item" v-for="(item, index) in imageList" :key="index"></image-block>
    </div>

    <v-progress-linear v-if="loading" :indeterminate="true"></v-progress-linear>
  </v-container>
</template>

<style>
  .image-list{
    display: flex;
    flex-wrap: wrap;
  }
</style>

<script>
    import ImageBlock from "../components/ImageBlock";
    export default {
        components: {ImageBlock},
        mounted() {
            this.axios.get('https://api.thecatapi.com/v1/images/search?limit=100&page=1&mime_types=jpg,png')
                .then(response => {
                    this.baseImageList = response.data
                    const images = [];
                    this.addImages()
                    for (let i = 0; i < this.baseImageList.length; i++) {
                        images[i] = new Image()
                        images[i].src = this.baseImageList[i].url
                    }
                })
            window.onscroll = () => {
                const bottomOfWindow = document.documentElement.scrollTop + window.innerHeight + 10 > document.documentElement.offsetHeight;

                if (bottomOfWindow && !this.loading) {
                    this.loading = true;

                    setTimeout(() => {
                        this.loading = false;
                        this.addImages()
                    }, 3000)
                }
            }
        },
        data: () => ({
            loading: false,
            imageList: [],
            baseImageList: [],
        }),
        methods: {
            onAboutClick() {
                this.$router.push({name: 'about'})
            },
            addImages() {
                const tmp = [];
                for (let i=0; i<30; i++) {
                    tmp.push(this.baseImageList[Math.floor(Math.random()*this.baseImageList.length)])
                }
                this.imageList = this.imageList.concat(tmp)
            }
        }
    }
</script>

