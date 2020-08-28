<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <HelloWorld @update="changeText" :msg="msg"/>
        parent:<input type="text" v-model="data.tail">
    </div>
</template>

<script>
    import HelloWorld from './components/Tools.vue'
    import {provide, ref,reactive} from 'vue'

    export default {
        name: 'App',
        data() {
            return {
                msg: ''
            }
        },
        setup() {
            const tail = ref('!')
            const data=reactive({
                tail:'!'
            })
            provide('tail', tail)
            provide('data', data)
            return {tail,data}
        },
        components: {
            HelloWorld
        },
        methods: {
            changeText() {
                this.msg = 'tim'
            }
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
