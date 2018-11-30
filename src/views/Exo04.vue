<template>
    <div id="Exo04">
        <!-- <button class="btn" @click="addImg">{{content}}</button> -->
        <button class="btn" @click="images++">{{content}}</button>
        <br>
        <!-- <img class="mt-5 myImages" src="../../public/img/chef-says-okay-clip-art_f.jpg" alt="a guy says okay" v-for="(image,index) in images" :key="index"> -->
        <img class="mt-5 myImages" src="../../public/img/chef-says-okay-clip-art_f.jpg" alt="a guy says okay" v-for="image in images" :key="image">
    </div>
</template>

<script>
export default {
    data(){
        return{
            content: "Click here to add an image",
            images: 0
            // images: [],
        }
    },  
    // methods:{
    //     addImg(){
    //         this.images.push(this.image)
    //     }
    // }
}
</script>

<style scoped>

.myImages{
    width: 100px;
    height: 100px;
}

</style>
