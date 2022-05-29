<script>
export default {
    data() {
        return {
            number:0,
            items:[1,2,3],
            color:""
        }
    },
    methods: {
        countup(){
            this.number = this.number + 1
        }
    },
    computed: {
        custom_color(){
            return this.color.toUpperCase();
        }
    }
}
</script>

<template>
<div>
    <h1>{{number}}</h1>
    <button @click="countup">countup</button>
    <p v-if="number">0以上</p>
    <p v-else>0</p>
    <ul>
        <li v-for="(item,index) in items" :key="index">{{item}}</li>
    </ul>
    <p :class="color">カラー</p>
    <input type="text" v-model="color">
    <p>{{custom_color}}</p>
</div>
</template>
<style>
.red {
    color: red;
}
.green {
    color: green;
}
.blue {
    color: blue;
}
</style>