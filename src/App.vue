<template>
    <div id="app">
        <h2 class="title" @click="initGame()">井字棋</h2>
        <div ref="checkerBoard" class="checker-board">
            <template v-for="(row,rowIndex) in map">
                <template v-for="(col,colIndex) in row">
                    <Cell @cellClick="cellClick(rowIndex,colIndex)" :status="status"/>
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
                status: '',
                map: [
                    [null, null, null],
                    [null, null, null],
                    [null, null, null]
                ]
            }
        },
        methods: {
            initGame() {
                this.totalCount = 0
                this.map = [[null, null, null],
                    [null, null, null],
                    [null, null, null]]
            },

            cellClick(rowIndex, colIndex) {
                this.status= this.totalCount % 2 ? 'X' : 'O'
                this.totalCount++
                this.map[rowIndex][colIndex] = this.status
                for (let row in this.map) {
                    if (this.map[row][0] !== null && this.map[row][0] === this.map[row][1] && this.map[row][1] === this.map[row][2]) {
                        return alertResult(this.map[row][0])
                    }
                    for (let col in this.map[row]) {
                        if (this.map[0][col] !== null && this.map[0][col] === this.map[1][col] && this.map[1][col] === this.map[2][col]) {
                            return alertResult(this.map[0][col])
                        } else if (this.map[0][0] !== null && this.map[0][0] === this.map[1][1] && this.map[1][1] === this.map[2][2]) {
                            return alertResult(this.map[1][1])
                        } else if (this.map[0][2] !== null && this.map[0][2] === this.map[1][1] && this.map[1][1] === this.map[2][0]) {
                            return alertResult(this.map[1][1])
                        }
                    }
                }

                //通报结果
                function alertResult(winner) {
                    setTimeout(() => {
                        alert(`winner is "${winner}"`)
                    })
                }

            }
        },
        mounted() {
            let checkerBoard = this.$refs.checkerBoard

            function resize() {
                checkerBoard.style.height = getComputedStyle(checkerBoard).width + ''
            }

            resize()
            window.addEventListener('resize', resize)
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
        font-size: calc(100 / 750 * 100vw);
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
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .checker-board {
        min-width: 300px;
        max-width: 500px;
        width: 3rem;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }

</style>
