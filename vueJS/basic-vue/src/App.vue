<template>
    <LittleComponents :sendProps1="title" :sendProps2="year" :sendProps3="obj" />

    <h1 :class="{um : isUm}" v-if="umIsAlive">true</h1>
    <h1 :class="{um : isUm}" v-if="!umIsAlive">false</h1>
    <button @click="umum">엄?</button>

    <!-- <div v-if="isOpacity" class="red"></div>

    <div v-if="isOpacity == true" class="blue"></div>
    
    <div v-else class="yellow"></div> -->ㅏ	


    <h3 @click="plus">{{ count }}</h3>

    <div v-show="count > 1" class="red"></div>
    <section v-show="count <= 1" class="blue"></section>
    <button @click="count++">+</button>
    <button @click="count--">-</button>

    <table border="1">
        <tr>
            <th>user id</th>
            <th>user name</th>
            <th>user gender</th>
        </tr>
        <tr v-for="(mem, i) in member" :key="i">
            <td>{{ mem.id }}</td>
            <td>{{ mem.name }}</td>
            <td>{{ mem.gender }}</td>
        </tr>
    </table>

    <h3> {{ num }} </h3>
    <h3> {{ num }} </h3>
    <button @click="plus"></button>

    <h2> {{ address }} </h2>

    <input type="text" v-model="yourName" placeholder="이름을 입력하시오">
    <p v-show="yourName != ''"> {{ yourName }} </p>
</template>

<script>
    import LittleComponents from './components/LittleComponents'

    export default {
        name: 'App',
        data() {
            return {
                isUm : false,
                umIsAlive : true, 
                isOpacity : true, 
                count : 1,
                num : 1, 
                member : [
                    {
                        id : 1, name : 'jhon', gender : 'male'
                    },
                    {
                        id : 2, name : 'sahra', gender : 'female'
                    },
                    {
                        id : 3, name : 'tom', gender : 'male'
                    },
                ], 
                address1 : '경기도', 
                address2 : '성남시', 
                address3 : '은행동', 
                yourName : '',
                title : '부모 컴포넌트에서 선언된 데이터',
                year : 2024, 
                obj : {
                    id : 3, 
                    name : 'Jhon', 
                }
            }
        }, 
        watch : {
            count: function() {
                alert('카운트 변수 변경!')
            }
            // watch 에선 함수명 : function() {함수내용}, 함수명() {함수내용} 모두 가능한듯.
        }, 
        computed : {
            address : function() {
                return `${this.address1} ${this.address2} ${this.address3}`
            }
        }, 
        methods: {
            umum() {
                this.isUm = !this.isUm
                this.umIsAlive = !this.isUm
            }, 
            plus() {
                this.num++
            }, 
            printName() {

            }
        },
        components: {
            LittleComponents, 
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

    .um {
        color: blue;
    }

    .red {
        width: 100px;
        height: 100px;
        background-color: red;
    }

    .blue {
        width: 100px;
        height: 100px;
        background-color: blue;
    }

    .yellow {
        width: 100px;
        height: 100px;
        background-color: yellow;
    }

    input + p {
        widows: 100px;
        height: 30px;
        background-color: lightblue;
    }
</style>
