<template>
    <div class="tab-bar-item" @click="tabClick">
        <div v-if="!isActive"><slot name="item-icon"></slot></div>
        <div v-else><slot name="item-icon-active"></slot></div>
        <div :style="activeStyle"><slot name="item-text"></slot></div>
    </div>
</template>

<script>
export default {
    props: {
        path: String,
        activeColor: {
            type: String,
            default: 'red'
        }
    },
    data() {
        return {}
    },
    computed: {
        isActive() {
            return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle() {
            return this.isActive ? { color: this.activeColor } : {}
        }
    },
    created() {},
    mounted() {},
    watch: {},
    methods: {
        tabClick() {
            this.$router.replace(this.path)
        }
    },
    components: {}
}
</script>

<style scoped>
.tab-bar-item {
    flex: 1;
    height: 49px;
    font-size: 14px;
    text-align: center;
}

.tab-bar-item img {
    width: 24px;
    height: 24px;
    margin: 3px 0 2px;
    vertical-align: middle;
}
</style>
