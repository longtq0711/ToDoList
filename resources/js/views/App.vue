<template>
    <div class="container">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <add-items v-on:reloadList="getList()"></add-items>
        </div>
        <list-view :items="items" v-on:reloadList="getList()"></list-view>
    </div>
</template>

<script>
    import AddItems from '../components/AddItems.vue';
    import ListView from '../components/ListView.vue';
    export default {
        components: {
            AddItems,
            ListView,
        },
        data() {
            return {
                items: []
            }
        },
        methods: {
            getList() {
                axios.get('api/items').then(response => {
                    this.items = response.data;
                }).catch(error => {
                    console.log(error);
                })
            }
        },
        created() {
            this.getList();
        }
    }
</script>
<style scoped>
    .container {
        width: 350px;
        margin: auto;
    }
    .heading {
        background: #e6e6e6;
        padding: 10px;
    }
    #title {
        text-align: center;
    }
</style>
