<template>

    <div class="Background">
        <div class="content">
            <div v-html="compiled"></div>
        </div>
    </div>

</template>
<script>
import marked from 'marked'
import background from './background.md'

export default {
    data() {
        return {
            source: background
        }
    },
    computed:{
        compiled(){
            return marked(this.source)
        }
    }
}

</script>
<style scoped>

.Background {
    width: 100%;
    /* height: 100%; */
}

h1 {
    font-size: 25px;
}

</style>
