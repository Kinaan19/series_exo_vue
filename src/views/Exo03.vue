<template>
    <div id="Exo03">
        <div class="myDivs my-3 mr-3"><div :class="{myInDivs : !x}"></div></div>
        <div class="myDivs my-3 ml-3"><div :class="{myInDivs : x}"></div></div>
        <br>
        <button class="btn px-3 my-3" @click="switchSquare">Click</button>
        <br>
        <span>{{content}}</span>
    </div>
</template>

<script>
export default {
    data(){
        return{
            content: "Push the button !!!",
            n: 0,
            x: false
        }
    },
    methods: {
        switchSquare(){
            this.x = !this.x;
            this.n++
            if(this.n <= 1){
                this.content = `You pushed the button ${this.n} time`;
            }else{
                this.content = `You pushed the button ${this.n} times`;
            }
        }
    }
}
</script>

<style scoped>

.myDivs{
    width: 300px;
    height: 100px;
    background-color: #000;
    display: inline-block;
    margin: 0 auto;
}

.myInDivs{
    width: 150px;
    height: 50px;
    background-color: #b60000;
    margin: 0 auto;
}

</style>


