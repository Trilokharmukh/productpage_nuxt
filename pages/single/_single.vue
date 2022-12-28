<template>
    <div>
        <div class="product-container">
            <div class="image-container">
                <div class="top-image">
                    <img :src="mainImage" />
                </div>
                <div class="bottom-images">
                    <img 
                        v-for="item of product.images" 
                        v-if="item!==mainImage"
                        :src="item" @click="changeImage(item)" 
                        :key = "item"
                        />
                </div>
            </div>
            <div class="product-details">
                <h1 class="product-title">{{ product.title }}</h1>
                <h3 class="product-brand">---{{ product.brand }}</h3>
                <div class="product-description">{{ product.description }}</div>
                <div class="product-price">Price: {{ product.price }}</div>
                <button @click="showData">Show data</button>
                <NuxtLink to="/">
                    <button>Back to home</button>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>


<style scoped>
.product-container {
    width: 80vw;
    background-color: rgb(236, 236, 236);
    /* height: 500px; */
    margin: 5px;
    margin: auto;
    margin-top: 10px;
    margin-bottom: 10px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;

}

.image-container {
    width: 500px;
    padding: 10px;
}

/* .top-image { */
    /* height: 400px; */
    /* border: 1px solid red; */
    /* box-shadow: 1px 1px 8px; */
/* } */

.top-image img {
    width: 100%;
    height: 400px;
    object-fit: contain;

}

.bottom-images {
    /* width: 400px; */
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    margin-top: 10px;

}

.bottom-images img {
    width: 20%;
    aspect-ratio: 1/1;
    object-fit: cover;
    margin: 5px;
}

.bottom-images img:hover {
    border: 1px solid rgb(98, 88, 243);
    scale: 1.2;
}

.product-details {
    max-width: 50%;
    padding: 10px;
    display: flex;
    flex-direction: column;
    /* align-items: center; */

}

.product-brand {
    color: rgb(187, 187, 100);
}

.product-description {
    padding-top: 20px;
    color: rgb(187, 187, 100)
}

.product-price {
    background-color: blue;
    width: 100px;
    color: white;
    margin: 10px 0;
}
</style>

<script>
export default {
    async asyncData({ params }) {
        // console.log("context",context);
        const product = await fetch(`https://dummyjson.com/products/${params.single}`)
            .then(res => res.json());
        
        let mainImage = product.images[product.images.length-1];
        return { product, mainImage }
    },

    methods: {
        showData: function () {
            console.log("Products: ", this.product);
            for (let item of this.product.images) {
                console.log("image link:", item);
            }
        },

        changeImage: function (img) {
            console.log("changeImage called..", img);
            this.mainImage = img;
        }
    },
}
</script>