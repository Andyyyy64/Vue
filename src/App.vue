<script>
export default {
    data(){
        return {
            list:[],
            addText:"",
            keyword:""
        }
    },
    methods: {
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
                return !todo.isChecked;
            });
        },
        filterLists(){
            var filtered=[];
            for(var i in this.list){
                var list = this.list[i];
                var text = this.addText
                if(list.text.indexOf(this.keyword) !== -1) {
                    filtered.push(list);
                }
            }
            return filtered;
        }
    },
    computed: {
        remaining(){
            var count = 0;
            var todos = this.list;
            var length = todos.length;
            for(var i = 0; i<length; i++){
                if(!todos[i].isChecked){
                    count++;
                }
            }
            return count;
        },
        filteredLists(){
            return this.filterLists();
        }
        
    }
}
</script>

<template>
<div class="container">
    <div>残タスク:{{remaining}}/{{list.length}}</div>
    <input type="text" v-model="addText" placeholder="ToDoを入力して">
    <button @click="addtodo">追加</button>
    <button @click="deleteBtn">削除</button>
    <input type="text" placeholder="キーボードを入力して" v-model="keyword"><hr>
    <div v-if="keyword !=='' ">
     <ul v-for="(list,index) in filterLists" :key="index">
       <li>
           <span :class="{done:list.isChecked}">
           <input type="checkbox" v-model="list.isChecked">{{list.text}}
           </span>
       </li>
     </ul>
    </div>
    <div v-else>
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
</div>
</template>