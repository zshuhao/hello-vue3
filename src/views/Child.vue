<template>
    <div>
        <h3>Child</h3>
        <div @click="handleChild">props: {{ test }}</div>
    </div>
</template>

<script>
import { getCurrentInstance } from 'vue'
export default {
    name: 'Child',
    props: {
        test: String
    },
    setup (props, context) {
        const instance = getCurrentInstance()
        const handleChild = () => {
            console.log(this)
            console.log(props)
            console.log(context)
            console.log(instance.ctx.$router)
        }

        return {
            handleChild
        }
    }

}
</script>
