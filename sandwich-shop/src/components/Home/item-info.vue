<template>
<b-container fluid v-on:"passIndex" class="inventory-item">
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
    props: ["name", "quantity", "image", "index"]

}
</script>

<style lang="scss">

</style>
