<template>
    <div id="Main">
        <div class="title">
            <h1>Individual Project</h1>
            <h2>Oskar Bunyan (ob14767/11960)</h2>
        </div>
        <div class="content">
            <h3><b>Topic: </b>Bayesian Optimisation With Relational Data</h3>
            <p>This project research and forwards a way of improving Bayesian Optimisation by including relational knowledge between locations in the input space.</p>
        </div>
        <background></background>
        <experiment1></experiment1>
        <experiment2></experiment2>
        <!-- <presentation></presentation> -->
    </div>
</template>

<script>
import background from './pages/background.vue'
import datasets from './pages/dataset.vue'
import presentation from './pages/presentation.vue'
import experiment1 from './pages/experiment1.vue'
import experiment2 from './pages/experiment2.vue'


export default {
    name: 'app',
    data () {
        return {
            msg: 'Welcome to Your Vue.js App'
        }
    },
    components: {
        background,
        datasets,
        presentation,
        experiment1,
        experiment2
    }
}
</script>

<style>
body {
    overflow-y: auto;
}

#Main {
    /* font-family: 'Avenir', Helvetica, Arial, sans-serif; */
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

#Main > div {
    margin: 20px auto;
}

h1, h2, h3 {
    font-weight: normal;
    display: block;
}

h1 {
    font-size: 30px;
    text-align: center;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    /* display: inline-block; */
    margin: 0 10px;
}

a {
    color: #42b983;
}

.title {
    margin-bottom: 20px;
}

.content {
    max-width: 900px;
    padding: 15px;
    margin: 0 auto;
    text-align: left;
}
</style>
