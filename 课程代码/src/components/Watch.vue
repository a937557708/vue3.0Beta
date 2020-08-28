<template>
    <div class="hello">
        <div v-for="item in result">{{item}}</div>
        <input type="text" v-model="keyword">
    </div>
</template>

<script>
    import {ref, watch} from 'vue'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        setup(props) {
            const keyword = ref('')
            const result = ref([])

            function getResult(keyword) {
                return setTimeout(function () {
                    result.value.push(keyword)
                }, 2000)
            }

            watch(() => props.msg, (c, p, onInvalidate) => {
                console.log('c:' + c, 'p:' + p)
                const timer = getResult(c)
                onInvalidate(() => {
                    clearTimeout(timer)
                })
            })
            return {keyword, result}
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
