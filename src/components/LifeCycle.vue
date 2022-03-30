<template>
    <div>
        <span>Vue的生命周期</span>
        n的值：{{n}}
        <button @click="n++">n+1</button>
        <button @click="fix">销毁Vue对象</button>
        <div>
            时间戳：{{time}}<br/>
<!--            格式化后的时间：{{fmtTime}}-->
        </div>
    </div>
</template>

<script>
    export default {
        name: "LifeCycle",
        data(){
          return {
              n:1,
              time:1648435823766
          }
        },
        beforeCreate() {
            console.log("beforeCreate");
        },
        created() {
            console.log("created");
        },
        beforeMount() {
            console.log("beforeMount:页面未经过Vue编译");
        },
        mounted() {
            console.log("mounted:Vue编译过的页面");
        },
        beforeUpdate() {
            console.log("beforeUpdated：数据是新的，但页面是旧的");
        },
        updated() {
            console.log("updated:数据和页面都是新的");
        },
        beforeDestroy() {
            console.log("beforeDestroy:在此阶段的数据操作都不会触发页面更新");
        },
        destroyed() {
            console.log("destroyed");
        },
        methods:{
            fix(){
                this.$destroy();
            }
        }
        // computed:{
        //     fmtTime(){
        //         return dayjs(this.time).format("yyyy-MM-dd hh:mm:ss")
        //     }
        // }
    }
</script>

<style scoped>

</style>