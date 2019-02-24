<template>
    <div :class="{active: active}" class="image-block" @mouseover="mouseover()" @mouseout="mouseout()">
        <img alt="" :src="item.url">
        <div class="hover" v-show="active"></div>
        <div class="hover content" v-show="active">
            <v-btn flat dark to="about">chat</v-btn>
        </div>
    </div>
</template>

<style scoped>
    .image-block {
        position: relative;
        flex-grow: 1;
        margin: 2px;
        height: 200px;
    }
    img {
        height: 200px;
        object-fit: cover;
        max-width: 100%;
        min-width: 100%;
        vertical-align: bottom;
    }
    .hover {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: black;
        opacity: 0.6;
    }
    .hover.content {
        background-color: transparent;
        color: white;
        opacity: 1;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>

<script>
    export default {
        props: [
            'item'
        ],
        data: () => ({
            active: false,
        }),
        methods: {
            mouseover() {
                this.active = true
            },
            mouseout() {
                this.active = false
            }
        }
    }
</script>
