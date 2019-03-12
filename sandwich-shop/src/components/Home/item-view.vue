<template>
<b-container fluid v-on:click="passIndex($event)" class="inventory-item p-0">
    <b-row>
        <b-col class="inventory-item__image">
            <img v-bind:src=image>
        </b-col>
    </b-row>
    <div class="inventory-item__text">
        <b-row class="inventory-item__text__name">
            <b-col>
                <h6>{{ name }}</h6>
            </b-col>
        </b-row>
        <b-row class="inventory-item__text__quantity">
            <b-col>
                <h6>Quantity: {{ quantity }}</h6>
                <h6>{{  }}</h6>
            </b-col>
        </b-row>
    </div>
</b-container>   
</template>

<script>
export default {
    props: ["name", "quantity", "image", "inventoryView", "index"],
    data() {
        return {
            
        }
    },
    methods: {
        passIndex: function() {
            this.$emit('changeView', false);
            
        }
    }
}


</script>

<style lang="scss">
    .inventory-item {
        box-shadow: 2px 3px 10px #888888;
        min-width: 100px;
        max-width: 200px;
        transition: 0.25s;
        border-radius: 5px;
        

        &:hover {
            cursor: pointer;
            transform: scale(1.1);
            transition: 0.25s;
        }

        &__image {
            img {
                max-width: 100%;
                height: auto;
                width: auto;
                border-top-left-radius: 5px;
                border-top-right-radius: 5px;
            }
        }
        &__text{
            padding: 5%;
            text-align: left;
        }
        
    }

</style>
