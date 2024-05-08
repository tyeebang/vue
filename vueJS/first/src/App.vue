<template>

    <nav class="menu">
        <a href="#">Home</a>
        <a href="#">Product</a>
        <a href="#">About us</a>
    </nav>
    
    <div class="item" v-for="(room, index) in roomData" :key="index">
        <img :src="room.image" :alt="index">
        <h3> {{ room.title }} </h3>
        <p> {{ room.price }}원 </p>
        <button @click="detailChange(index)">자세히보기</button>
        <p> {{ detailIsTrue[index] }} </p>
        <section class="detail" v-if="detailIsTrue[index]">
            <div>
                <img :src="room.image" :alt="index">
                <h3> {{ room.title }} </h3>
                <h6> {{ room.content }} </h6>
                <p> {{ room.price }}원 </p>
                <button @click="detailChange(index)">X 닫기</button>
            </div>
        </section>
    </div>
</template>

<script setup>
    import {roomData} from "./assets/data.js";

    import { ref } from "vue"

    const detailIsTrue = ref([false, false, false, false, false, false])

    const detailChange = (index) => {
        detailIsTrue.value[index] = !detailIsTrue.value[index]
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    nav.menu {
        width: 100%;
        height: 100px;
        background-color: darkslateblue;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .menu a {
        color: white;
        text-decoration: none;
        margin: 0 30px;
    }

    .item {
        width: 50%;
        margin: 0 auto;
    }

    .item > img {
        width: 100%;
    }

    .detail {
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background-color: rgba(0, 0, 0, .5);
    }

    .detail div {
        background-color: #fff;
        width: 600px;
        height: 400px;
        padding: 15px;
    }

    .detail img {
        width: 70%;
    }
</style>
