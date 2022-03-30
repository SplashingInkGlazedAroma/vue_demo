<template>
<div>
    <div class="basic" :class="mood" @click="changeMood">{{name}}</div>
    <div :style="styleObj">样式</div>
</div>
</template>

<script>
    export default {
        name: "ClassAndStyle",
        data(){
            return{
                mood:"normal",
                styleObj:{
                    fontSize:'40px',
                    backgroundColor:'pink'
                }
            }
        },
        props:{
            name:String
        },
        methods:{
            changeMood(){
                const arr=['normal','sad','yellow'];
                let index=Math.floor(Math.random()*3);
                this.mood=arr[index];
            }
        }
    }
</script>

<style scoped>
    .basic{
        height: 200px;
        text-align: center;
        background-color: black;
    }
    .normal{
        background-color: red;
    }
    .sad{
        background-color: green;
    }
    .happy{
        background-color: yellow;
    }
</style>