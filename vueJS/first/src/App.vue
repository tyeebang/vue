<template>

    <nav class="menu">
        <a href="#">Home</a>
        <a href="#">Product</a>
        <a href="#">About us</a>
    </nav>

    <div v-for="(prtd, i) in roomData" :key="i">
        <img :src="prtd.image" alt="room">
        <h3 @click="isModalTrue[i] = true"> {{ prtd.title }} </h3>
        <p> {{ prtd.price }} </p>
        <section class="modal" v-if="isModalTrue[i]">
            <div>
                <h3> {{ prtd.title }} </h3>
                <p> 상세 페이지 내용임 </p>
                <button @click="isModalTrue[i] = false">X 닫기</button>
            </div>
        </section>
    </div>
</template>

<script>
    import {roomData} from "./assets/data.js";

    export default {
        name: 'App',
        data() {
            return {
                roomData, 
                isModalTrue : [false, false, false, false, false]
            }
        },
        methods: {

        },
        components: {

        }
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

    .menu {
        background-color: darkslateblue;
        padding: 15px;
        border-radius: 5px;
    }

    .menu a {
        color: white;
        padding: 10px;
        text-decoration: none;
    }

    img {
        width: 50%;
        margin: 30px;
    }

    body {
        position: relative;
    }

    .modal {
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        background-color: rgba(0, 0, 0, .5);
        width: 100vw;
        height: 100vh;
    }

    .modal div {
        width: 600px;
        height: 200px;
        border-radius: 15px;
        background-color: #fff;
        z-index: 100000;
    }

    .modal button {
        width: 100px;
        height: 40px;
        margin-left: 450px; 
        margin-top: 40px;
        border: none;
        background-color: #333;
        color: #fff;
        border-radius: 15px;
        cursor: pointer;
    }
</style>
