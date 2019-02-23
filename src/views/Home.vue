<template>
  <v-container fluid>
    <v-toolbar flat>
      <label>Free stock photos</label>
      <v-btn>Tendances</v-btn>
      <v-btn>Nouveautés</v-btn>
    </v-toolbar>

    <div class="image-list">
      <img alt="" :src="'https://xieranmaya.github.io/images/cats/'+item.url" v-for="item in imageList">
    </div>

    <v-progress-linear v-if="loading" :indeterminate="true"></v-progress-linear>
  </v-container>
</template>

<style>
  .image-list{
    display: flex;
    flex-wrap: wrap;
  }
  .image-list img{
    height: 200px;
    flex-grow: 1;
    object-fit: cover;
    margin: 8px;
  }
</style>

<script>
    export default {
        mounted() {
            this.imageList = this.imageList.concat(this.baseImageList)
            window.onscroll = () => {
                const bottomOfWindow = document.documentElement.scrollTop + window.innerHeight + 10 > document.documentElement.offsetHeight;

                if (bottomOfWindow) {
                    this.loading = true;

                    setTimeout(() => {
                        this.loading = false;
                        this.imageList = this.imageList.concat(this.baseImageList)
                    }, 5000)
                }
            }
        },
        data: () => ({
            loading: false,
            imageList: [],
            baseImageList: [
                {
                    "url": "photo-103450229.jpg",
                },
                {
                    "url": "photo-108273877.jpg",
                },
                {
                    "url": "photo-115203323.jpg",
                },
                {
                    "url": "photo-23583825.jpg",
                },
                {
                    "url": "stock-photo-123942383.jpg",
                },
                {
                    "url": "stock-photo-124559545.jpg",
                },
                {
                    "url": "stock-photo-132046989.jpg",
                },
                {
                    "url": "stock-photo-132118343.jpg",
                },
                {
                    "url": "stock-photo-132311221.jpg",
                },
                {
                    "url": "stock-photo-132586903.jpg",
                },
                {
                    "url": "stock-photo-135203031.jpg",
                },
                {
                    "url": "stock-photo-135626379.jpg",
                },
                {
                    "url": "stock-photo-136947953.jpg",
                },
                {
                    "url": "stock-photo-138378295.jpg",
                },
                {
                    "url": "stock-photo-138436811.jpg",
                },
                {
                    "url": "stock-photo-142950305.jpg",
                },
                {
                    "url": "stock-photo-143046061.jpg",
                },
                {
                    "url": "stock-photo-143181649.jpg",
                },
                {
                    "url": "stock-photo-144530143.jpg",
                },
                {
                    "url": "stock-photo-144730939.jpg",
                },
                {
                    "url": "stock-photo-145414771.jpg",
                },
                {
                    "url": "stock-photo-146038669.jpg",
                },
                {
                    "url": "stock-photo-146231033.jpg",
                },
                {
                    "url": "stock-photo-146914861.jpg",
                },
                {
                    "url": "stock-photo-147877407.jpg",
                },
                {
                    "url": "stock-photo-147969173.jpg",
                },
                {
                    "url": "stock-photo-148015373.jpg",
                },
                {
                    "url": "stock-photo-148704233.jpg",
                },
                {
                    "url": "stock-photo-148928293.jpg",
                },
                {
                    "url": "stock-photo-148950715.jpg",
                },
                {
                    "url": "stock-photo-21951271.jpg",
                },
                {
                    "url": "stock-photo-21964829.jpg",
                },
                {
                    "url": "stock-photo-22618399.jpg",
                },
                {
                    "url": "stock-photo-31201539.jpg",
                },
                {
                    "url": "stock-photo-34598868.jpg",
                },
                {
                    "url": "stock-photo-47252094.jpg",
                },
                {
                    "url": "stock-photo-51980510.jpg",
                },
                {
                    "url": "stock-photo-55601508.jpg",
                },
                {
                    "url": "stock-photo-65681789.jpg",
                },
                {
                    "url": "stock-photo-70461471.jpg",
                },
                {
                    "url": "stock-photo-71801901.jpg",
                },
                {
                    "url": "stock-photo-71913567.jpg",
                },
                {
                    "url": "stock-photo-72223295.jpg",
                },
                {
                    "url": "stock-photo-72620185.jpg",
                },
                {
                    "url": "stock-photo-74402039.jpg",
                },
                {
                    "url": "stock-photo-75097491.jpg",
                },
                {
                    "url": "stock-photo-75186237.jpg",
                },
                {
                    "url": "stock-photo-79250373.jpg",
                },
                {
                    "url": "stock-photo-79692589.jpg",
                },
                {
                    "url": "stock-photo-7979718.jpg",
                },
                {
                    "url": "stock-photo-7980252.jpg",
                },
                {
                    "url": "stock-photo-81390687.jpg",
                },
                {
                    "url": "stock-photo-81988949.jpg",
                },
                {
                    "url": "stock-photo-83149705.jpg",
                }
            ],
        })
    }
</script>

