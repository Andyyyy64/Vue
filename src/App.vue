<script>
export default {
    data() {
        return {
            number:0
        }
    },
    methods: {
        countup(){
            this.number = this.number + 1
        }
    }
}
</script>

<template>
<div>
    <h1>{{number}}</h1>
    <button @click="countup">countup</button>
</div>
</template>