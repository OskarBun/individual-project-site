<template>

    <div class="Research">
        <div class="title">
            <h1>Research</h1>
        </div>
        <div class="content">
            <div v-html="compiled"></div>
        </div>
    </div>

</template>
<script>
import marked from 'marked'
import research from './research.md'

export default {
    data() {
        return {
            source: research
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

.Research {
    width: 100%;
    /* height: 100%; */
}

h1 {
    font-size: 25px;
}

</style>
