<template>
    <div>
        <h2>Vue事件处理</h2>
        <button v-on:click="showInfo">单击事件</button>
        <br/>
        <button @:click="showInfo2($event,66)">单击事件</button>
        <br/>
        <a href="https://www.baidu.com" @click.prevent="prevent">百度</a>
        <div class="girl">
            <div>
                <button @click.stop="stop">阻止冒泡事件</button>
            </div>
            <div>
                <button @click.once="once">一次性事件</button>
            </div>
        </div>
        <div>
            firstName:<input v-model="firstName" type="text"/><br/>
            lastName:<input v-model="lastName" type="text"/><br/>
            fullName:<span>{{ fullName }}</span>
        </div>
        <div>
            <h3>今天天气很{{ info }}</h3><br/>
            <button @click="changeWeather">切换天气</button>
        </div>
        <div>
            a的值是：{{numbers.a}}<br/>
            <button @click="numbers.a++">a+1</button><br/>
            b的值是：{{numbers.b}}<br/>
            <button @click="numbers.b++">b+1</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Event",
        data() {
            return {
                isHot: Boolean,
                numbers:{
                    a:1,
                    b:2
                }
            }
        },
        props: {
            firstName: String,
            lastName: String
        },
        methods: {
            showInfo(event) {
                console.log(event);
                console.log(event.target.innerText);
            },
            showInfo2(event, number) {
                console.log(event);
                console.log(number);
            },
            prevent() {
                console.log("阻止事件的默认行为");
            },
            stop() {
                console.log("阻止事件的冒泡行为");
            },
            once() {
                console.log("一次性事件");
            },
            changeWeather() {
                return this.isHot = !this.isHot;
            }
        },
        computed: {
            fullName: {
                get() {
                    return this.firstName + '-' + this.lastName;
                },
                set(val) {
                    let arr = val.split('-');
                    this.firstName = arr[0];
                    this.lastName = arr[1];
                }
            },
            info() {
                return this.isHot ? "炎热" : "凉爽";
            }
        },
        watch: {
            info: {
                handler(newVal, oldVal) {
                    setTimeout(()=>{
                        console.log(newVal, oldVal);
                    },2000);
                }
            },
            numbers:{
                deep:true,
                handler(){
                    console.log("numbers里面的内容改变了");
                }
            }
        }
    }
</script>

<style scoped>
    * {
        margin-top: 20px;
    }
</style>