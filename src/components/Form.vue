<template>
    <div>
        <div>
            <form @submit.prevent="submitForm">
                <label>
                    账号：<input type="text" v-model.trim="userInfo.account">
                </label><br/>
                <label>
                    密码：<input type="password" v-model="userInfo.password">
                </label><br/>
                <label>
                    性别：男<input type="radio" name="sex" v-model="userInfo.sex" value="1">
                    女<input type="radio" name="sex" v-model="userInfo.sex" value="0">
                </label><br/>
                <label>
                    年龄：<input type="number" name="age" v-model.number="userInfo.age">
                </label><br/>
                <label>
                    爱好：游泳<input type="checkbox" v-model="userInfo.hobbies" value="swim">
                    滑雪<input type="checkbox"  v-model="userInfo.hobbies" value="skating">
                    溜冰<input type="checkbox"  v-model="userInfo.hobbies" value="skiing">
                    跳水<input type="checkbox"  v-model="userInfo.hobbies" value="diving">
                </label><br/>
                <select v-model="userInfo.city">
                    <option value="请选择校区">请选择校区</option>
                    <option value="0">上海</option>
                    <option value="1">北京</option>
                    <option value="2">天津</option>
                    <option value=“3>杭州</option>
                </select><br/>
                其他信息：
                <textarea v-model.lazy="userInfo.otherInfo"></textarea><br/>
                <input type="checkbox"  v-model="userInfo.agreeFlag">阅读并同意<a href="https://www.google.com">《用户协议》</a><br/>
                <button>提交</button>
            </form>
        </div>
        <div v-text="name"></div>
        <div v-html="msg"></div>
        <div v-once>初始值：{{n}}</div>
        <div>
            当前的值：{{n}}
        </div>
        <button @click="n++">n+1</button>
        <div v-pre>Vue只会解析这一段一次，加快解析</div>
        <div ref="info">{{message}}</div>
        <button @click="showDom">获取上方DOM</button>
    </div>
</template>

<script>
    export default {
        name: "Form",
        data(){
            return{
                userInfo:{
                    account:'',
                    password:'',
                    sex:0,
                    age:18,
                    hobbies:[],
                    city:'',
                    otherInfo:'',
                    agreeFlag:''
                },
                name:'画江湖之不良人',
                msg:'<h2>进击的巨人</h2>',
                n:1,
                message:"画江湖之灵主"
            }
        },
        methods:{
            submitForm(){
                console.log(JSON.stringify(this.userInfo));
            },
            showDom(){
                console.log(this.$refs.info);
            }
        }
    }
</script>

<style scoped>

</style>