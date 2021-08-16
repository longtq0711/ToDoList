<template>
    <div>
        <div v-for="(item,key) in items" :key="key">
            <list-item :item="item" class="item" v-on:itemchanged="$emit('reloadList')"></list-item>
        </div>
    </div>
</template>
<script>
    import ListItem from '../components/ListItem.vue';

    export default {
        props:['items'],
        components: {
            ListItem
        }
    }
</script>
<style scoped>
    .item {
        background: #e6e6e6;
        padding: 5px;
        margin-top: 5px;
    }
</style>
