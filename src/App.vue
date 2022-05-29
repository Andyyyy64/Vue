<script>
export default {
    data(){
        return {
            count:0
        }
    },
    methods: {
        countincrement(){
            this.count = this.count + 1
        }
    }
}
</script>

<template>
<div>
    <h1>{{count}}回クリックされました</h1>
    <button @click="countincrement">increment</button>
</div>
</template>