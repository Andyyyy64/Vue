<script>
export default{
    data(){
        return {
            addText:"",
            list:[]
        }
    },
    methods:{
        addtodo(){
            if(this.addText !== ""){
                this.list.push({
                    text:this.addText,
                    isChecked:false,
                });
            }
            this.addText = "";
        },
        deleteBtn(){
            this.list = this.list.filter(function(todo){
                return !todo.isChecked
            })
        }
    },
    computed:{
        remaining(){
            var count = 0;
            var todos = this.list;
            var length = todos.length;
            for(var i=0;i<length;i++){
                if(!todos[i].isChecked){
                    count++
                }
            }
            return count;
        }
    }
}
</script>

<template>
<div class="container">
    <div>残りタスク:{{remaining}}/{{list.length}}
    </div>
    <input type="text" v-model="addText" placeholder="ToDoを入力して">
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
    <div v-else>現在のタスクはありません</div>
</div>
</template>         