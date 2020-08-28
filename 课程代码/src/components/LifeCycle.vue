<template>
    <div class="hello">
        <h1>{{ data.title }}</h1>
        <input type="text" v-model="data.title">
    </div>
</template>

<script>
    import {reactive, watch, onMounted, onBeforeMount, onRenderTriggered} from 'vue'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        setup(props) {
            const data = reactive({
                title: ''
            })
            onMounted(() => {
                console.log('onMounted')
            })
            onBeforeMount(() => {
                console.log('onBeforeMount')
            })
            onRenderTriggered((e) => {
                console.log(e)
            })
            return {data}
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
