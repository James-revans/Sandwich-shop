<template>
<b-container fluid v-if="inventory[itemIndex]">
    <b-row class="home">
        <b-col>
            <button @click="returnHome($event)">Home</button>
        </b-col>
    </b-row>
    <div class="item-info text-center">
        <b-row class="">
            <b-col class="item-info__image">
                <!-- <img v-bind:src=itemImage> -->
                <img v-bind:src=inventory[itemIndex].image>
            </b-col>
        </b-row>
        <div class="item-info__text">
            <b-row>
                <b-col>
                    <h6>{{ inventory[itemIndex].name }}</h6>
                </b-col>
            </b-row>
            <b-row class="item-info__text__quantity">
                <b-col>
                    <h6>Quantity: <button @click="inventory[itemIndex].quantity += 1">+</button> {{ inventory[itemIndex].quantity }} <button @click="inventory[itemIndex].quantity -= 1">-</button></h6>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <h6>Update Details</h6>
                </b-col>
            </b-row> 
            <b-row>
                <b-col>
                    <h6>Delete Item</h6>
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
            
        }
    },

    methods: {
        returnHome: function() {
            this.$emit('changeView', true);
        }
    }

}
</script>

<style lang="scss">

.item-info {
    margin: auto;
    max-width: 400px;
    box-shadow: 2px 3px 10px #888888;
    border-radius: 5px;

    &__image {
        img {
            max-width: 100%;
            height: auto;
            width: auto;
            border-top-left-radius: 5px;
            border-top-right-radius: 5px;
        }
    }

    &__text {
        text-align: left;
        padding: 5%;

        &__quantity {
            button {
                width: 24px;
                height: 24px;
                border-radius: 5px;
                background: rgb(75, 174, 231);
                border: solid thin rgb(255, 255, 255);
                font-weight: 600;
                color: white;
                padding: 0;
            }
        }
    }

}

.home {
    button {
    position: relative;
    top: 20px; 
    background: white;
    border: none;
    font-weight: 400;
    transition: 0.1s;

    &:hover {
    transform: scale(1.05);
    transition: 0.1s;
    }
}

}



</style>
