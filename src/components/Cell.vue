<template>
    <div ref="cell" class="cell" @click="cellClick()" :style="{color:itemStatus==='X'? 'red':''}">{{itemStatus}}</div>
</template>

<script>
    export default {
        name: "Cell",
        props: ['status'],
        data() {
            return {
                itemStatus: ""
            }
        },
        methods: {
            cellClick() {
                if (this.itemStatus === "") {
                    this.$emit('cellClick')
                    this.$nextTick(()=>{
                        this.itemStatus = this.status
                    })
                }
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
