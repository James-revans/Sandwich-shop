<template>
<b-container fluid :inventoryView="inventoryView">
    <b-row v-show="inventoryView" class="">
        <b-col cols="12" class="inventory-blocks d-flex justify-content-center align-intems-center">
            <Item v-for="(item, index) in inventory" :key='index'
            :name="item.name"
            :quantity="item.quantity"
            :image="item.image"
            :index="index"
            v-on:changeView="select($event, index)"
            class="m-3"/>
        </b-col>
    </b-row>
    <b-row v-show="!inventoryView"> 
        <b-col cols="12" class="d-flex justify-content-center align-intems-center">
            <Info
            :inventory="inventory"
            :itemIndex="itemIndex"
            v-on:changeView="select($event)"
            class=""
            />
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
            inventoryView: true,
            itemIndex: null
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
    },
    methods: {
        select: function(event, index) {
            this.inventoryView = !this.inventoryView;
            this.itemIndex = index;
            
        }
    } 
}
</script>

<style lang="scss">
    .inventory-blocks {
        flex-wrap: wrap;
    }

</style>
