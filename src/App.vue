<script>
export default {
    data(){
        return {
            items:[1,2,3],
            show: true
        }
    },
}
</script>

<template>
<div>
    <button @click="show = !show">togglelist</button>
    <ul v-if="show">
        <li v-for="(item,index) in items" :key="index">{{item}}</li>
    </ul>
    <p v-else>list is not empty but hidden</p>
</div>
</template>