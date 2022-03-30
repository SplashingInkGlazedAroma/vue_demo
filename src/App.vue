<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <HelloWorld msg="Welcome to Your Vue.js App"/>
        <Element name="Vue"   google_url="https://www.google.com"  king="李星云"  queen="姬如雪"/>
        <Event first-name="李" last-name="星云" is-hot="true"/>
        <ClassAndStyle name="testClassAndStyle" />
        <List></List>
        <Form></Form>
        <lifeCycle></lifeCycle>
        <MySlot>
            <ul v-for="(g,index) in games" :key="index">
                {{g}}
            </ul>
        </MySlot>
        <MySlot>
            <template slot="food">
                <ol  v-for="(f,index) in food" :key="index">
                    {{f}}
                </ol>
                <div>更多美食</div>
            </template>
            <template v-slot:animation>
                <h4 v-for="(a,index) in animation" :key="index">
                    {{a}}
                </h4>
                <div>更多动漫</div>
            </template>
        </MySlot>
        <MySlot>
            <template  scope="source">
                <ul v-for="(f,index) in source.friends" :key="index">{{f}}</ul>
                <ol v-for="(m,index) in source.money" :key="index">{{m}}</ol>
            </template>
        </MySlot>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'
    import Element from "@/components/Element"
    import Event from "@/components/Event"
    import ClassAndStyle from "@/components/ClassAndStyle"
    import List from '@/components/List'
    import Form from "@/components/Form"
    import LifeCycle from "@/components/LifeCycle"
    import MySlot from "@/components/MySlot";


    export default {
        name: 'App',
        data() {
            return {
                games:['王者荣耀','英雄联盟','决战平安京'],
                food:['羊肉串','驴肉火锅','臭豆腐'],
                animation:['灵笼','进击的巨人','大剑','剑风传奇']
            }
        },
        components: {
            ClassAndStyle,
            HelloWorld,
            Element,
            Event,
            List,
            Form,
            LifeCycle,
            MySlot
        },
        mounted() {
            console.log("App",this);
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
