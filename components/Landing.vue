<template>
    <div>
        <Search @products="getProduct" />

        <p v-if="$fetchState.pending">Loading....</p>
        <p v-else-if="$fetchState.error">Error while fetching mountains</p>
        <Product v-else :mountains="mountains" />

    </div>
</template>

<script>
export default {
    data() {
        return {
            mountains: [],
            product: "",
        }
    },

    methods: {
        async getProduct(value) {
            console.log(value);
            this.product = value;

            this.mountains = await fetch(
                `https://dummyjson.com/products/search?q=${this.product}`
            ).then(res => res.json())

            console.log("Products: ", this.mountains.products);

        }
    },

    async fetch() {
        this.mountains = await fetch(
            `https://dummyjson.com/products/`
        ).then(res => res.json())

        console.log("moun", this.mountains.products);
    },
}
</script>