<template>
<b-container fluid v-if="inventory[itemIndex]">
    <b-row>
        <b-col>
            <button @click="returnHome($event)">Home</button>
        </b-col>
    </b-row>
    <div class="inventory-item">
        <b-row>
            <b-col class="inventory-item__image text-center">
                <!-- <img v-bind:src=itemImage> -->
                <img v-bind:src=inventory[itemIndex].image>
            </b-col>
        </b-row>
        <div class="inventory-item__text">
            <b-row class="inventory-item__text__name">
                <b-col>
                    <h6>{{ inventory[itemIndex].name }}</h6>
                </b-col>
            </b-row>
            <b-row class="inventory-item__text__quantity">
                <b-col>
                    <h6>On Hand: {{ inventory[itemIndex].quantity }}</h6>
                </b-col>
            </b-row>
        </div>         
    </div>       
    
</b-container>

</template>

<script>
export default {
    props: ["inventory", "itemIndex", "inventoryView", "image"],
    data() {
        return {
            viewChange: true,
            // itemName: '',
            // itemQuantity: '',
            // itemImage: ''
            
        }
    },

    //  Erros occur right now when accessing properties of the inventory array in the template above. 
    //  Attempting to fix this with computed properties below

    // copmuted: {
    //     itemName: function() {
    //         return this.inventory[itemIndex].name
    //     },
    //     itemQuantity: function() {
    //         return this.inventory[itemIndex].quantity
    //     },
    //     itemImage: function() {
    //         return this.inventory[itemIndex].image
    //     }
        
    // },
    methods: {
        returnHome: function() {
            this.$emit('changeView', true);
        }
    }

}
</script>

<style lang="scss">


</style>
