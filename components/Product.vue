<template>
    <div>
        <div>
            <div v-if="mountains.products.length === 0">
                <h1 style="text-align: center; margin-top: 40px;">Not found</h1>
            </div>
            <div v-else>
                <div class="product-container">
                    <div 
                        v-for="mountain of mountains.products" 
                        class="container" 
                        :key="mountain.id"
                    >
                        <div class="image-container">
                            <img :src="mountain.images[mountain.images.length-1]" />
                        </div>

                        <h3 class="title">
                            {{ mountain.title }} 
                        </h3>

                        <div class="description">
                            {{ mountain.description }}
                        </div>

                        <div>Price: {{ mountain.price }}</div>

                        <NuxtLink :to="`/single/${mountain.id}`">
                            <button class="view-product">View Product</button>
                        </NuxtLink>
                    </div>

                </div>

            </div>

        </div>
        <!-- </div> -->
    </div>
</template>

<style scoped>
.product-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 20px;

}

.container {
    background-color: rgba(248, 227, 220, 0.815);
    width: 250px;
    margin: 15px;
    padding: 10px;
    box-sizing: border-box;
    border-radius: 5px;
}

.image-container {
    width: 100%;
    height: 200px;
}

.image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    /* padding: 10px; */
    box-sizing: border-box;
}

.title {
    padding-top: 5px;
    height: 50px;
}

.description {
    margin-top: 5px;
    margin-bottom: 5px;
    color: darkolivegreen;
    max-height: 37px;
    overflow: hidden;
}

.view-product {
    width: 100%;
    background-color: blue;
    color: white;
    border: none;
    height: 30px;
    margin-top: 10px;
    margin-bottom: 15px;
    border-radius: 10px;
    cursor: pointer;
}
</style>

<script>
export default {
    props: ['mountains']
}
</script>