<template>
    <div>
        <lightBox :lightStatus="lightStatus[0]" :i="getIndex(0)"  @toggleLight="toggleLight"/>
        <lightBox :lightStatus="lightStatus[1]" :i="getIndex(1)"  @toggleLight="toggleLight"/>
        <lightBox :lightStatus="lightStatus[2]" :i="getIndex(2)"  @toggleLight="toggleLight"/>
    </div>
</template>

<script>
    import lightBox from './LightBox.vue';
export default {
    components: {lightBox},
    props: ['lightStatus', 'row'],
    methods: {
        getIndex(num){
            return num + (parseInt(this.row) *3);
        },
        toggleLight(lightObj) {
            this.$emit('toggleLight', lightObj);
        }
    }
}
</script>

<style scoped>
    div {
        display: flex;
    }
</style>