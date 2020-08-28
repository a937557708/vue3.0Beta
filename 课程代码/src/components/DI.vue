<template>
    <div class="hello">
        <h1>{{ data.title }}{{data1.tail}}</h1>
        <input type="text" v-model="data.title">
    </div>
</template>

<script>
    import {reactive, inject, watch, onMounted, onBeforeMount, onRenderTriggered} from 'vue'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        // inject:['tail'],
        setup(props) {
            const tail = inject('tail', '?')
            const data1 = inject('data', {})
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
            return {data,data1, tail}
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
