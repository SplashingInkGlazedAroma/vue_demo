<template>
    <div class="hello">
        <h1>Hello,{{ name }}</h1>
        <a :href="google_url">Google</a><br/>
        <div>
            单向绑定：<input type="text" v-bind:value="king"/><br/>
            双向绑定：<input type="text" v-model="queen"/><br/>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Element",
        props: {
            name: String,
            google_url: String,
            king: String,
            queen: String
        }
    }
</script>

<style scoped>

</style>