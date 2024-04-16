<template>
    <img alt="Vue logo" src="./assets/logo.png">

    <div>
        <h3> {{ product[0] }} </h3>
         <p>{{ price[0] }}만원</p>
    </div>
    <div>
        <h3> {{ product[1] }} </h3>
         <p>{{ price[1] }}만원</p>
    </div>
    <div>
        <h3> {{ product[2] }} </h3>
         <p>{{ price[2] }}만원</p>
    </div>
</template>

<script>

    export default {
        name: 'App',
        data() {
            return {
                product : [
                    '역삼동 원룸', '마포구 원룸', '천호동 원룸'
                ], 
                price : [
                    50, 70, 60
                ]
            }
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
    margin-top: 60px;
}
</style>
