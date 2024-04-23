<template>
    {{ sendProps1 }}
    {{ sendProps2 }} 
    {{ sendProps3.id }} 
    {{ sendProps3.name }} 
</template>

<script>
export default {
    data() {
        return {

        }
    }, 
    props : {
        sendProps1 : String,
        sendProps2 : Number, 
        sendProps3 : Object, 
    }
}
</script>

<style>

</style>