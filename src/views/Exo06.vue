<template>
    <div id="Exo06">
        <div>
            <input type="text" v-model="content">
            <button class="btn m-2" @click="addItem">Add a task to do</button>
            <br>
            <button class="btn m-2" @click="displayButton('todo')">Todo</button>
            <button class="btn m-2" @click="displayButton('doing')">Doing</button>
            <button class="btn m-2" @click="displayButton('done')">Done</button>
            <button class="btn m-2" @click="displayButton('deleted')">Deleted</button>
            <button class="btn m-2" @click="displayButton('all')">All</button>
            <ul>
                <todo ref="test" v-for="(el,index) in items" :key="index" :myContent="el"></todo>
            </ul>
        </div>
    </div>
</template>

<script>
    import todo from "../components/LiTodoList.vue"
export default {
    components:{
        todo
    },
    data(){
        return{
            content: "",
            items: [],
            elems: [],
            displayState: true
        }
    },
    methods:{
        addItem(){
            this.items.push(this.content);
            this.content = "";
            this.displayState = true;
            this.elems.forEach(element => {
                element.style.display = "";
            });
        },
        buttonFct(bg){
            if(this.displayState == true){
                this.displayState = false;
                this.elems.forEach(element => {
                    if(element.classList.contains(bg) == false){
                        element.style.display = "none";
                    }else{
                        element.style.display = "";
                    }
                });
            }else{
                this.elems.forEach(element => {
                    if(element.classList.contains(bg)){
                        if(this.displayState == false && element.style.display == ""){
                            element.style.display = "none";
                        }else{
                            element.style.display = "";
                        }
                    }
                });
            };
            
        },
        displayButton(btn){
            this.elems = Array.from(this.$el.getElementsByTagName("li"));
            switch (btn) {
                case "todo":
                    this.buttonFct("bg-dark");
                    break;
                case "doing":
                    this.buttonFct("bg-warning");
                    break;
                case "done":
                    this.buttonFct("bg-success");
                    break;
                case "deleted":
                    this.buttonFct("bg-danger");
                    break;
                case "all":
                    this.displayState = true;
                    this.elems.forEach(element => {
                        element.style.display = "";
                    });
                    break;   
            }
        }
    } 
}
</script>

<style scoped>

</style>