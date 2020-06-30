<template>
    <div class="test">
        <h1>test page</h1>
        <div>count: {{ count }}</div>
        <div>count2: {{ count2 }}</div>
        <button @click="add">add</button>
        <button @click="add2">add2</button>
        <div ref="dom" @click="clickDom">dom</div>
        <child test="123"></child>
    </div>
</template>

<script>
import { ref, onUpdated, watchEffect } from 'vue'
import Child from './Child'
export default {
    name: 'Test',
    components: { Child },
    setup (props, context) {
        const count = ref(0)
        const count2 = ref(0)
        const dom = ref(null)

        const add = () => {
            console.log('add')
            count.value++
        }

        const add2 = () => {
            console.log('add2')
            count2.value++
        }

        const clickDom = () => {
            console.log(props)
            console.log(context)
            console.log(dom.value)
        }

        watchEffect(() => {
            console.log(count.value)
        })

        watchEffect(() => {
            console.log(count2.value)
        })

        onUpdated(() => {
            console.log('updated')
        })

        return {
            count,
            count2,
            add,
            add2,
            dom,
            clickDom
        }
    }
}
</script>

<style lang="less" scoped>
.test {
  color: red;
}
</style>
