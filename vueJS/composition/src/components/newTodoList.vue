<template>
    <section>
        <h3> TODO LIST </h3>
        
        <div class="fn_tab">
            <button> ADD TASK </button>

            <select id="checkState">
                <option value="all">all</option>
                <option value="checked">complete</option>
                <option value="unchecked">not yet</option>
            </select>
        </div>

        <ul class="list">
            <li>
                <div>
                    <input type="checkbox" id="check">
                    <label for="check"></label>
                    <div class="list_txt">
                        <h6>make TodoList</h6>
                        <p>2024-05-08</p>
                    </div>
                </div>
                <div class="btn_list">
                    <button>delete</button>
                    <button>modify</button>
                </div>
            </li>
        </ul>

        <ul>
            <li>1</li>
            <li>2</li>
        </ul>
    </section>
</template>

<script setup>
    
</script>

<style scoped>

</style>