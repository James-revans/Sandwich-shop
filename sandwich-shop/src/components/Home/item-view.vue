<template>
<b-container fluid @click="passIndex($event)"  class="inventory-item">
    <b-row>
        <b-col class="inventory-item__image text-center">
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
                <h6>On Hand: {{ quantity }}</h6>
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

            this.$emit('passIndex', this.index)

        }
    }
}


</script>

<style lang="scss">
    .inventory-item {
        box-shadow: 2px 3px 10px #888888;
        min-width: 100px;
        max-width: 200px;

        &:hover {
            cursor: pointer;
            transform: scale(1.1);
            transition: 0.25s;
        }

        &__image {
            height: 75px;
            width: 50px;
            img {
                height: 100%;
                width: auto;
            }
        }
        &__text{
            padding-top: 15px;
            text-align: left;
        }
        
    }

</style>
