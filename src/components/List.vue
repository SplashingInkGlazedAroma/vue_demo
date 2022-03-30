<template>
    <div>
        <div>
            <h2> 当前num的值：{{num}}</h2>
            <button @click="num++">num++</button>
            <div v-if="num===1">Angular</div>
            <div v-else-if="num===2">React</div>
            <div v-else-if="num===3">Freemarker</div>
            <div v-else>Vue</div>
        </div>
        <div>
            遍历对象数组
            <ul v-for="(p,index) in persons" :key="p.id">
                <li>{{index}}----{{p.name}}----{{p.age}}</li>
            </ul>
            遍历对象
            <ul>
                {{car.color}}--{{car.price}}--{{car.weight}}
            </ul>
            遍历字符串数组
            <ul v-for="(hobby,index) in hobbies" :key="index">
                {{hobby}}
            </ul>
        </div>
        <div>
            人员列表：
            <input type="text" placeholder="请输入搜索条件（姓名）" v-model="keyword">
            <button @click="sortType=0">原顺序</button>
            <button @click="sortType=1">年龄升序</button>
            <button @click="sortType=2">年龄降序</button>
            <ul v-for="p in filPeoples" :key="p.id">
                <li>{{p.name}}---{{p.age}}--{{p.sex}}</li>
            </ul>
        </div>
        <div>
            学生信息：<br/>
            <ol>
                <li>姓名：{{student.name}}</li>
                <li>年龄：{{student.age}}</li>
                <li v-if="student.sex">性别：{{student.sex}}</li>
            </ol>
            <button @click="addSex">添加学生性别</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "List",
        data(){
            return{
                num:1,
                persons:[
                    {id:'001',name:"李星云",age:25},
                    {id:'002',name:"姬如雪",age:22},
                    {id:'003',name:"陆林轩",age:20},
                    {id:'004',name:"张子凡",age:23},
                ],
                car:{
                    color:'红色',
                    price:2000000,
                    weight:"400KG"
                },
                peoples:[
                    {id:'001',name:"唐三",age:25,sex:'男'},
                    {id:'002',name:"小舞",age:22,sex:'女'},
                    {id:'003',name:"宁荣荣",age:24,sex:'女'},
                    {id:'004',name:"戴沐白",age:22,sex:'男'},
                    {id:'005',name:"朱竹清",age:20,sex:'女'},
                    {id:'006',name:"唐昊",age:40,sex:'男'},
                ],
                keyword:'',
                sortType:0  ,//0原顺序，1升序，2降序
                hobbies:['抽烟','喝酒','烫头'],
                student:{
                    name:'张三',
                    age:26
                }
            }
        },
        computed:{
            filPeoples(){
                    const arr=this.peoples.filter(p=>{
                        return p.name.indexOf(this.keyword)!==-1;
                    });
                    if(this.sortType){
                        arr.sort((p1,p2)=>{
                            return this.sortType===1?p1.age-p2.age:p2.age-p1.age
;                            })
                    }
                    return arr;
                }
        },
        methods:{
            addSex(){
               return  this.$set(this.student,'sex','男');
            }
        }
    }
</script>

<style scoped>

</style>