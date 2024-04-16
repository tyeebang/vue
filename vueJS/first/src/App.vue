<template>
    <nav class="menu">
        <a v-for="(menu, i) in ['Home', 'Product', 'About us']" :key="i" href="#"> {{ menu }} </a>
        <!-- <a href="#">Product</a>
        <a href="#">About us</a> -->
    </nav>

    <!-- <div>
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
    </div> -->

    <div v-for="(prtd, i) in product" :key="i">
        <h3> {{ prtd }} </h3>
        <p> {{ price[i] }} </p>
        <button @click = reportAdd(i)> 허위 매물 신고 </button> <span>신고수 : {{ report[i] }}</span>
    </div>
</template>

<script>

    export default {
        name: 'App',
        data() {
            return {
                product : [
                    '역삼동 원룸', '마포구 원룸', '천호동 원룸', '은행동 원룸'
                ], 
                price : [
                    50, 70, 60, 40
                ],
                report : [
                    0, 0, 0, 0
                ]
            }
        },
        methods: {
            reportAdd(i) {
                this.report[i]++
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
</style>
