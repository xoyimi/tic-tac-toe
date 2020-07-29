<template>
    <div id="app">
        <template v-for="row in map">
            <template v-for="(row,index) in row">
                <Cell @cellClick="cellClick(index)"/>
            </template>
        </template>
    </div>
</template>

<script>
    import Cell from "./components/Cell";

    export default {
        name: 'App',
        components: {
            Cell
        },
        data() {
            return {
                count: 0,
                map: [
                    [null, null, null],
                    [null, null, null],
                    [null, null, null]
                ]
            }
        },
        methods: {
            cellClick(index) {
                console.log(index)
            }
        }
        ,
        created() {
        }
    }
</script>

<style>

    :root {
        touch-action: none;
        height: 100%;
        font-size: calc(750 / 100 * 100vw);
    }

    body {
        margin: 0;
        height: 100%;
        font-size: calc(12px + .5vw);
    }

    #app {

    }
</style>
