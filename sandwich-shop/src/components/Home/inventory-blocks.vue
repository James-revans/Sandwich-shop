<template>
<b-container fluid :inventoryView="inventoryView">
    <b-row v-if="inventoryView" class="">
        <b-col cols="12" class="inventory-blocks d-flex justify-content-center align-intems-center">
            <Item v-for="(item, index) in inventory" :key='index'
            :name="item.name"
            :quantity="item.quantity"
            :image="item.image"
            :index="index"
            class="m-3"/>
        </b-col>
    </b-row>
    <b-row v-else> 
        <b-col>
            <Info/>
        </b-col>
    </b-row>
</b-container>
    
</template>

<script>

import Item from "@/components/Home/item-view.vue";
import Info from "@/components/Home/item-info.vue";
import axios from "axios";

export default {
    components: {
        Item,
        Info
    },
    data() {
        return {
            inventory: [],
            inventoryView: true
        }
    },
    created() {
        var self = this
        axios.get('https://api.myjson.com/bins/83ajm')
        .then(function (response) {
            self.inventory = response.data;
            console.log(response);
        })
        .catch(function (error) {
            console.log(error);
        });
    }
}
</script>

<style lang="scss">
    .inventory-blocks {
        flex-wrap: wrap;
    }

</style>
