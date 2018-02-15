<template>

    <div class="Experiment1">
        <div class="content">
            <div v-html="compiled"></div>
        </div>
    </div>

</template>
<script>
import marked from 'marked'
import experiment from './experiment2.md'

export default {
    data() {
        return {
            source: experiment
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

.Experiment1 {
    width: 100%;
    /* height: 100%; */
}

h1 {
    font-size: 25px;
}

</style>
