<template>
    <div class="cell" @click="cellClick">{{status}}</div>
</template>

<script>
    export default {
        name: "Cell",
        data() {
            return {
                status: ''
            }
        },
        props: ['totalCount'],
        methods: {
            cellClick() {
                this.status === '' ? this.$emit('cellClick') : ''
                this.status = this.totalCount % 2 ? 'X' : 'O'
            }
        }
    }
</script>

<style scoped>
    .cell {
        flex-basis: calc(350px / 3);
        height: calc(350px / 3);
        border: 1px solid pink;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: .02rem;
    }
</style>
