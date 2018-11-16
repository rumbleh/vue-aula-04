<template>
    <div>
        <ul class="list-group">
            <li class="list-group-item" v-for="item in items" :key="item.ProductId">
                {{ item.Name }} - {{ Number(item.Price) }}
                <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">
                    Remove from cart
                </button>
            </li>
        </ul>
        <div class="card my-5 p-3">
            <h4 class="text-center">R$ {{ total  }}</h4>
        </div>
        <button :disabled="items.length === 0" @click="$emit('pay')" class="btn btn-info form-control">Pay</button>
    </div>
</template>

<script>
    export default {

        props: ['items'],

        computed: {
            total(){
                return this.items.reduce((acc, item) => acc + Number(item.Price), 0)
            }
        }
    }
</script>

<style>
</style>
