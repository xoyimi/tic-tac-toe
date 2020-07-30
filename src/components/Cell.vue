<template>
    <div ref="cell" class="cell" @click="cellClick()">{{status}}</div>
</template>

<script>
    export default {
        name: "Cell",
        props: ['status'],
        methods: {
            cellClick() {
                if (this.status ==='X') {
                        this.$refs.cell.style.setProperty('color', 'red')
                }
                this.$emit('cellClick')
            }
        }
    }
</script>

<style scoped>
    .cell {
        flex-basis: 33.33%;
        height: 33.33%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: calc(40px + .5vw);
        outline: purple 2px solid;
        outline-offset: -1px;
    }

</style>
