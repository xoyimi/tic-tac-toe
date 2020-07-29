<template>
    <div id="app">
        <h2 class="title">井字棋</h2>
        <div class="checker-board">
            <template v-for="(row,rowIndex) in map">
                <template v-for="(col,colIndex) in row">
                    <Cell @cellClick="cellClick(rowIndex,colIndex)" :totalCount="totalCount"/>
                </template>
            </template>
        </div>
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
                totalCount: 0,
                map: [
                    [null, null, null],
                    [null, null, null],
                    [null, null, null]
                ]
            }
        },
        methods: {
            cellClick(rowIndex, colIndex) {
                this.totalCount++
                console.log(this.totalCount)
            }
        }
        ,
        created() {
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;

    }

    :root {
        touch-action: none;
        height: 100%;
        font-size: calc(750 / 100 * 100vw);
    }

    body {
        margin: 0;
        height: 100%;
        font-size: calc(12px + .5vw);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #app {
        height: 100%;
        width: 100%;
    }

    .checker-board {
        width: 350px;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }

    .title {
        text-align: center;
        width: 100%;
    }
</style>
