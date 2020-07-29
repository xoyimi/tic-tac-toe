<template>
    <div class="cell" @click="cellClick">{{status}}</div>
</template>

<script>
    export default {
        name: "Cell",
        data(){
            return{
                status:''
            }
        },
        methods:{
            cellClick(){
                this.status='X'
                this.$emit('cellClick')
            }
        }
    }
</script>

<style scoped>
.cell{
    max-width: 200px;
    max-height: 200px;
    height: 25vw;
    width: 25vw;
    border: 1px solid pink;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: .02rem;
}
</style>
