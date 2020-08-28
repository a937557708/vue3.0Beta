<template>
    <div class="hello">
        <div v-for="(item,index) in result" :ref="el=>{divs[index]=el}">{{item}}</div>
        <input type="text" v-model="keyword">
        <button @click="show">show</button>
    </div>
</template>

<script>
    import {ref, watchEffect} from 'vue'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        setup() {
            const keyword=ref('')
            const result=ref([])
            const divs=ref([])
            function getResult(keyword){
                if (!keyword){
                    return
                }
                return setTimeout(function () {
                    result.value.push(keyword)
                },2000)
            }
            function show(){
                console.log(divs.value[1])
            }
            watchEffect((onInvalidate)=>{
                const timer = getResult(keyword.value)
                onInvalidate(()=>{
                   // clearTimeout(timer)
                })
            })
            return {keyword,result,divs,show}
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
