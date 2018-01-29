<template>
    <div id="Main">
        <div class="title">
            <h1>Individual Project</h1>
            <h2>Oskar Bunyan ob14767</h2>
        </div>
        <div class="content">
            <h3><b>Topic: </b>Bayesian Optimisation With Relational Data</h3>
            <h3><b>Data: </b>?</h3>
        </div>
        <background></background>
        <datasets></datasets>
    </div>
</template>

<script>
import background from './pages/background.vue'
import datasets from './pages/dataset.vue'

export default {
    name: 'app',
    data () {
        return {
            msg: 'Welcome to Your Vue.js App'
        }
    },
    components: {
        background,
        datasets
    }
}
</script>

<style>
#Main {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    overflow-y: auto;
}

h1, h2, h3 {
    font-weight: normal;
    display: block;
}

h1 {
    font-size: 30px;
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
