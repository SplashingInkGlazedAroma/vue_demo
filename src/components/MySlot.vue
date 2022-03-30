<template>
    <div>
        <slot></slot>
        <slot name="food"></slot>
        <slot name="animation"></slot>
        <slot :friends="friends" :money="money"></slot>
    </div>

</template>

<script>
    export default {
        name: "MySlot",
        data(){
            return{
                friends:['李星云','姬如雪','张子凡','陆林轩'],
                money:['人民币','美元','英镑','欧元']
            }
        }
    }
</script>

<style scoped>

</style>