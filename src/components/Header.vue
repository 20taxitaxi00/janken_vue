<template>
    <div>
        <h1>{{ title }}</h1>
        <ul class="nav">
            <li>
               <router-link to="/game" class="btn navBtn">ゲーム</router-link>
            </li>
            <li>
               <router-link to="/score" class="btn navBtn">成績</router-link>
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    name: 'header',
    data() {
        return {
            title: 'ジャンケンゲーム'
        }
    }
}
</script>


<style scoped>

</style>