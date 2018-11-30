<template>
    <div id="Exo05">
        <div>
            <input id="firstInput" class="my-2 bg-dark" type="text" disabled="disabled" v-model="content1">
            <br>
            <input id="secondInput" class="my-2" type="text" disabled="disabled" v-model="content2">
            <br>
            <button class="btn btn-light" @click="buttonFct('7')">7</button>
            <button class="btn btn-light" @click="buttonFct('8')">8</button>
            <button class="btn btn-light" @click="buttonFct('9')">9</button>
            <button class="btn btn-warning" @click="buttonFct('+')">+</button>
            <br>
            <button class="btn btn-light" @click="buttonFct('4')">4</button>
            <button class="btn btn-light" @click="buttonFct('5')">5</button>
            <button class="btn btn-light" @click="buttonFct('6')">6</button>
            <button class="btn btn-warning" @click="buttonFct('-')">-</button>
            <br>
            <button class="btn btn-light" @click="buttonFct('1')">1</button>
            <button class="btn btn-light" @click="buttonFct('2')">2</button>
            <button class="btn btn-light" @click="buttonFct('3')">3</button>
            <button class="btn btn-warning" @click="buttonFct('*')">*</button>
            <br>
            <button class="btn btn-light" @click="buttonFct('0')">0</button>
            <button class="btn btn-light" @click="buttonFct('.')">.</button>
            <button class="btn btn-danger" @click="buttonFct('C')">C</button>
            <button class="btn btn-warning" @click="buttonFct('/')">/</button>
            <br>
            <button id="equal" class="btn btn-success" @click="buttonFct('=')">=</button>
        </div>
    </div>
</template>

<script>
import mexp from "../../node_modules/math-expression-evaluator/dist/browser/math-expression-evaluator.js"

export default {
    data(){
        return{
            content1: "",
            content2: "",
            result: "",
            operators: ["+","-","*","/"],
            checkOp: ""
        }
    },
    methods:{
        buttonFct(btn){
            this.checkOp = this.operators.some(el => this.content1.slice(-1).includes(el));
            switch (btn) {
                case "*":
                case "/":
                case "+":
                    if(this.content1.includes("=")){
                        this.content2 = this.result + btn;
                        this.content1 = this.content2;
                        this.content2 = "";
                    }else if(this.content2.slice(-1) == "" || this.content2.slice(-1) == "-"){
                    }else{
                        this.content2 += btn;
                        this.content1 += this.content2;
                        this.content2 = "";
                    };
                    break;
                case "-":
                    if(this.content2 == "" && this.content1 == ""){
                        this.content2 = btn;
                    }else if(this.content1.includes("=")){
                        this.content2 = this.result + btn;
                        this.content1 = this.content2;
                        this.content2 = "";
                    }else if(this.content2.slice(-1) == "" || this.content2.slice(-1) == "-"){
                    }else{
                        this.content2 += btn;
                        this.content1 += this.content2;
                        this.content2 = "";  
                    };
                    break;
                case "=":
                    if(this.content1.includes("=") || this.content1 == ""){
                    }else if(this.checkOp && this.content2 == ""){
                    }else{
                        this.content1 += this.content2;
                        this.content2 = "";
                        this.result = mexp.eval(this.content1);
                        this.content1 += " = " + this.result;
                    };
                    break;
                case "C":
                    this.content1 = "";
                    this.content2 = "";
                    break;
                default:
                    if(this.content1.includes("=")){
                        this.content1 = "";
                    };
                    this.content2 += btn;
                    break;
            }
        }
    }
}
</script>

<style scoped>

#Exo05 div{
    background-color: rgb(59, 109, 90);
    height: 650px;
    width: 30%;
    margin: 0 auto 25px auto;
    text-align: center;
    border-radius: 15px;
}

#equal{
    width: 410px;
    height: 100px;
}

input{
    width: 410px;
    height: 50px;
    border: none;
    padding: 15px;
    border-radius: 4px;
}

#firstInput{
    color: #fff;
    height: 100px;
    padding: 0 15px;
}

.btn{
    width: 100px;
    height: 75px;
    margin: 2px;
    box-shadow: none !important;
}

</style>