<template>
    <div class="hello">
        <h1>{{title}}</h1>
    </div>
</template>

<script>
    import {ref, unref, reactive, toRef, toRefs,isRef,isProxy,readonly,isReactive,isReadonly} from 'vue'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        setup() {
             const title=ref('hello')
           // console.log(isRef(title))
            const data = reactive({
                title: 'hello'
            })
            console.log(isReadonly(readonly(data)))
            // const titleRef=toRef(data,'title')
            // titleRef.value='world'
            // console.log(title)
            // console.log(unref(title))
            return {...toRefs(data)}
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
