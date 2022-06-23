<template>
    <div :class="lightEffect" @click="toggleLight">
    </div>
</template>

<script>
export default {
    props:['lightStatus', "i"],
    computed: {
        lightEffect() {
            if (this.lightStatus == 1) {
                return 'turned-on'
            } else {
                return 'turned-off'
            }
        }
    },
    methods: {
        toggleLight() {
            this.$emit('toggleLight', {
                'index': this.i,
                'status': !this.lightStatus
            });
        }
    }
}
</script>

<style scoped>
    div {
        width: 100px;
        height: 100px;
        border: 1px black solid;
    }
    .turned-off {
        background-color: aqua;
    }

    .turned-on {
        background-color: yellow;
    }
</style>