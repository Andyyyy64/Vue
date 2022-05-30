<script>
export default {
    data(){
        return {
            list:[],
            addtext:"",
            keyword:""
        }
    },
    methods: {
        addtodo(){
            if(this.addtext !== ""){
                this.list.push({
                    text:this.addtext,
                    isChecked:false,
                });
            }
            this.addtext = "";
        },
        deleteBtn(){
            this.list = this.list.filter(function(todo){
                return !todo.isChecked;
            });
        }
    }
}
</script>

<template>
<div class="container">
    <input type="text" v-model="addtext" placeholder="ToDoを入力して">
    <button @click="addtodo">追加</button>
    <button @click="deleteBtn">削除</button>
    <div v-if="list.length">
        <ul v-for="(todo,index) in list" :key="index">
            <li>
                <span :class="{done:todo.isChecked}">
                <input type="checkbox" v-model="todo.isChecked">{{todo.text}}
                </span>
            </li>
        </ul>
    </div>
    <div v-else>現在タスクはありません</div>
</div>
</template>