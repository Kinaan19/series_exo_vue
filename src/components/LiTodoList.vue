<template>
    <li :class="{'bg-dark' : todoState, 'bg-warning' : doingState, 'bg-success' : doneState, 'bg-danger' : deleteState}" >
        <input type="text" v-model="myContent" :disabled="editState">
        <button class="btn mx-2" v-if="editState" @click="todoFct"><i class="fas fa-clipboard-list"></i></button>
        <button class="btn mx-2" v-if="editState" @click="doingFct"><i class="fas fa-file-signature"></i></button>
        <button class="btn mx-2" v-if="editState" @click="doneFct"><i class="fas fa-clipboard-check"></i></button>
        <button class="btn mx-2" v-if="editState" @click="editFct"><i class="far fa-edit"></i></button>
        <button class="btn mx-2" v-if="editState" @click="deleteFct"><i class="far fa-trash-alt"></i></button>
        <button class="btn mx-2" v-if="!editState" @click="editFct"><i class="fas fa-check"></i></button>
    </li>
</template>

<script>
export default {
    props:{
        myContent:{
            type: String,
            required: true
        },
    },
    data(){
        return{
            editState: true,
            todoState: true,
            doingState: false,
            doneState: false,
            deleteState: false,
        }
    },
    methods:{
        todoFct(){
            this.doingState = false;
            this.doneState = false;
            this.deleteState = false;
            this.todoState = true;
        },
        doingFct(){
            this.todoState = false;
            this.doneState = false;
            this.deleteState = false;
            this.doingState = true;
        },
        editFct(){
            this.editState = !this.editState;
        },
        doneFct(){
            this.todoState = false;
            this.doingState = false;
            this.deleteState = false;
            this.doneState = true;
        },
        deleteFct(){
            this.todoState = false;
            this.doingState = false;
            this.doneState = false;
            this.deleteState = true;
        }
    }
}
</script>

<style scoped>

li{
    padding: 10px;
    list-style: none;
}

</style>