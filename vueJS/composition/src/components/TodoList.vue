<template>
    <section id="todo">
        <h3>TODO LIST</h3>

        <div>
            <button @click="setAddTap">Add Task</button>
            <div v-show="stateAddTap" class="pop">
                <div>
                    <h3>Add Task</h3>
                    <span>title &nbsp;: <input type="text" name="addTitle" v-model="addTitle" maxlength="24"></span>
                    <span>date : <input type="date" name="addDate" :min="day" v-model="addDate"></span>

                    <div>
                        <button @click="addList">complete</button>
                        <button @click="setAddTap">cancel</button>
                    </div>
                </div>
            </div>
            <select id="isChecked" v-model="state" @change="stateChange">
                <option value="all">all</option>
                <option value="checked">complete</option>
                <option value="not-checked">not yet</option>
            </select>
        </div>

        <ul>
            <li v-for="(data, index) in todoList" :key="index" v-show="data.canSee">
                <div>
                    <input type="checkbox" name="state" :id="index" class="isDo" @change="checkChange(index)">
                    <label :for="index"></label>
                    <p><span> {{ data.title }} </span><br> {{ data.date }} </p>
                </div>
                <div>
                    <button @click="deleteList(index)">delete</button>
                    <button @click="setModifyTab(index)">modify</button>
                    <div v-show="data.isTrue" class="pop">
                        <div>
                            <h3>modify list</h3>
                            <span>title &nbsp;: <input type="text" :name="index" :value="data.title" v-model="modifyTitle"></span>
                            <span>date : <input type="date" :name="index" :value="data.date" :min="day" v-model="modifyDate"></span>
                            <div>
                                <button @click="modifyList(index)">complete</button>
                                <button @click="setModifyTab(index)">cancel</button>
                            </div>
                        </div>
                    </div>
                </div>
            </li>
        </ul>
        <p>
            <a v-for="(num, index) in countTodo" :key="index" v-bind:href="`?page=${index+1}`"> &nbsp;{{ index+1 }}&nbsp; </a>
        </p>
    </section>
</template>

<script setup>
import { onMounted, ref } from "vue";
    // todo list 정보
    const todoList = ref([
        {
            title : '1', 
            date : '2024-05-08', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '2', 
            date : '2024-05-30', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '3', 
            date : '2024-05-08', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '4', 
            date : '2024-05-30', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '5', 
            date : '2024-05-08', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '6', 
            date : '2024-05-30', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '7', 
            date : '2024-05-08', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '8', 
            date : '2024-05-30', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '9', 
            date : '2024-05-08', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '10', 
            date : '2024-05-30', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '11', 
            date : '2024-05-08', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
        {
            title : '12', 
            date : '2024-05-30', 
            isTrue : false, 
            thisState : false, 
            canSee : false, 
        }, 
    ])

    onMounted(() => {
        paging()
    })

    // 페이징 변수
    const sum = ref(0)
    let countTodo = ref(Math.ceil(todoList.value.length / 5))
    if(countTodo.value == 0) {
        countTodo.value = 1
    }
    const queryString = ref(window.location.search.substring(6))
    if(queryString.value == '') {
        queryString.value = '1'
    }

    // 날짜 가져오기
    let today = new Date()
    let year = today.getFullYear()
    let month = today.getMonth() + 1
    if(month.toString().length == 1) {
        month = '0' + month
    }
    let date = today.getDate()
    if(date.toString().length == 1) {
        date = '0' + date
    }
    const day = ref(`${year}-${month}-${date}`)
    
    // 각종 변수 선언

    let stateAddTap = ref(false)
    
    let addTitle = ''
    let addDate = ''
    
    let modifyTitle = ''
    let modifyDate = ''
    
    let state = 'all'

    // 함수 선언
    const paging = () => {
        for(let i = 0; i < 5; i++) {
            let j = 0
            j = i + ((queryString.value - 1) * 5)
            
            if(todoList.value[j] != undefined) {
                todoList.value[j].canSee = true
            } else {
                break
            }
        }
    }

    const getCount = () => {
        sum.value = 0
        todoList.value.forEach(item => {
            if(item.canSee == true) {
                sum.value += 1
            }
        })

        countTodo.value = Math.ceil(sum.value / 5)
        if(countTodo.value == 0) {
            countTodo.value = 1
        }
    }

    const selectState = () => {
        let i = 0
        if(state == 'all') {
            todoList.value.forEach(item => {
                if(i < 5) {
                    item.canSee = true
                    i++
                }
            })
        } else if(state == 'checked') {
            todoList.value.forEach(item => {
                if(item.thisState == true) {
                    if(i < 5) {
                        item.canSee = true
                        i++
                    } else {
                        item.canSee = false
                    }
                } else {
                    item.canSee = false
                }
            })
        } else if(state == 'not-checked') {
            todoList.value.forEach(item => {
                if(item.thisState == false) {
                    if(i < 5) {
                        item.canSee = true
                        i++
                    } else {
                        item.canSee = false
                    }
                } else {
                    item.canSee = false
                }
            })
        }
    }

    const stateChange = () => {
        selectState()
        getCount()
    }

    const checkChange = (index) => {
        todoList.value[index].thisState = !todoList.value[index].thisState
        selectState()
        getCount()
    }

    const setAddTap = () => {
        stateAddTap.value = !stateAddTap.value
        addTitle = ''
        addDate = ''
    }

    const addList = () => {
        if(confirm('정말 리스트를 추가하시겠습니까?')) {
            if(addTitle != '' && addDate != '') {
                todoList.value.push({title : addTitle, date : addDate, isTrue : false, thisState : false, canSee : false})
                setAddTap()
                console.log(todoList.value)
            } else {
                alert('데이터에 빈곳이 있네요')
            }
        }
    }

    const setModifyTab = (index) => {
        if(todoList.value[index].isTrue == false) {
            modifyTitle = todoList.value[index].title
            modifyDate = todoList.value[index].date
        }
        todoList.value[index].isTrue = !todoList.value[index].isTrue
    }

    const modifyList = (index) => {
        if(confirm(`${index+1}번째 데이터를 정말 수정하시겠어요?`)) {
            if((modifyTitle == todoList.value[index].title && modifyDate == todoList.value[index].date)) {
                alert('두 데이터 모두 변함이 없어요!')
            } else {
                todoList.value[index].title = modifyTitle
                todoList.value[index].date = modifyDate
                alert('수정 완료')
                todoList.value[index].isTrue = !todoList.value[index].isTrue
            }
        }
    }
    
    const deleteList = (index) => {
        if(confirm(`${index + 1}번째 데이터를 정말 삭제하시겠어요?`)) {
            todoList.value.splice(index, 1)
            alert(`${index + 1}번째 항목이 삭제되었습니다.`)
        }
    }
</script>

<style scoped>

    #todo {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        width: 75vw;
        height: 60vh;
        margin: 0 auto;
        background-color: mediumpurple;
    }

    #todo > h3 {
        height: 10%;
        line-height: calc(60vh / 10);
        color: #fff;
        font-size: 2em;
    }

    #todo > div {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 95%;
        height: 10%;
        margin: 0 auto;
    }

    #todo > div > button {
        width: 10%;
        height: 90%;
        border: none;
        border-radius: 15px;
        color: purple;
        font-size: 1.1em;
        cursor: pointer;
    }

    #todo select {
        width: 15%;
        height: 90%;
        border: none;
        border-radius: 10px;
        padding: 5px;
        outline: none;
        color: purple;
        font-size: 1.1em;
    }

    #todo ul {
        width: 95%;
        height: 60%;
        margin: 0 auto;
        background-color: lemonchiffon;
        padding: 15px;
    }

    #todo li {
        display: flex;
        justify-content: space-between;
        padding: 0 1%;
        width: 100%;
        height: calc((60vh * 0.6 - 30px) * 0.2 - 10px);
        margin-bottom: 10px;
        border-bottom: purple 1.5px solid;
    }

    #todo li > div {
        display: flex;
        align-items: center;
    }

    #todo li > div:first-child {
        width: 40%;
    }

    #todo > ul > li > div:first-child > input {
        display: none;
    }

    #todo label {
        width: 1.4vw;
        height: 3vh;
        border: 1.5px solid purple;
        margin: 0 15px;
    }

    .isDo:checked + label::before {
        content: '✔';
        color: purple;
    }

    .isDo:checked ~ p span {
        text-decoration: line-through violet;
        font-style: italic;
    }

    #todo li p {
        width: 300px;
        text-align: left;
        color: purple;
    }

    #todo li p > span {
        font-weight: bold;
        font-size: 1.2em
    }

    #todo li > div:nth-child(2) {
        width: 20%;
        justify-content: space-around;
    }

    #todo li div:nth-child(2) > button {
        width: 40%;
        height: 80%;
        border: none;
        background-color: purple;
        color: white;
        font-size: 1.3em;
        border-radius: 15px;
    }

    .pop {
        position: fixed;
        top: 0;
        left: 0;
        display: flex;
        justify-content:center;
        align-items: center;
        width: 100vw;
        height: 100vh;
        background-color: rgba(0, 0, 0, .5);
        z-index: 100000;
    }
    
    .pop > div {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        width: 30%;
        height: 30%;
        background-color: #fff;
    }

    .pop button {
        width: 20%;
        height: 100%;
        border: none;
        border-radius: 15px;
        color: white;
        font-size: 1.2em;
        background-color: purple;
    }

    .pop > div > div {
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        width: 100%;
        height: 15%;
    }

    .pop h3 {
        font-size: 1.6em;
    }

    .pop span {
        font-size: 1.2em;
        height: 15%;
        color: mediumpurple;
        font-size: 1.6em;
    }

    .pop input {
        width: 50%;
        height: 100%;
        border: 1.5px solid mediumpurple;
        border-radius: 15px;
        outline: none;
        padding: 15px;
        font-size: .8em;
        background-color: #fff;
        color: purple;
    }
</style>