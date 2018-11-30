<template>
    <li :class="{'bg-dark' : elem.todoState, 'bg-warning' : elem.doingState, 'bg-success' : elem.doneState, 'bg-danger' : elem.deleteState}" >
        <input type="text" v-model="elem.name" :disabled="editState">
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
    props: ["elem"],
    data(){
        return{
            editState: true,
        }
    },
    methods:{
        todoFct(){
            this.elem.doingState = false;
            this.elem.doneState = false;
            this.elem.deleteState = false;
            this.elem.todoState = true;
        },
        doingFct(){
            this.elem.todoState = false;
            this.elem.doneState = false;
            this.elem.deleteState = false;
            this.elem.doingState = true;
        },
        editFct(){
            this.editState = !this.editState;
        },
        doneFct(){
            this.elem.todoState = false;
            this.elem.doingState = false;
            this.elem.deleteState = false;
            this.elem.doneState = true;
        },
        deleteFct(){
            this.elem.todoState = false;
            this.elem.doingState = false;
            this.elem.doneState = false;
            this.elem.deleteState = true;
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