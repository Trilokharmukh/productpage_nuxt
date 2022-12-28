<template>
    <div>
        <div class="search-container">
            <input 
                type="text" placeholder="search product" 
                class="search-box" 
                @keyup.enter="getInputData"
                v-model="inputData" />
            <button @click="clearData">Clear {{ inputData }}</button>
        </div>
    </div>
</template>

<style scoped>
.search-container {
    width: 70%;
    margin: auto;
    margin-top: 20px;

}

.search-box {
    width: 85%;
    /* margin: auto; */
    height: 50px;
    border-radius: 10px;
    font-size: 20px;
    border: 1px solid rgb(153, 150, 150);
}

.search-box:focus {
    outline: none;
    border: 1px solid rgb(165, 165, 241);

}

.search-container button {
    width: 10%;
    height: 40px;
    border-radius: 10px;
    border: 1px solid rgb(153, 150, 150);

}
</style>

<script>
export default {
    data() {
        return {
            inputData: "",
        }
    },
    methods: {
        getInputData:function(){
            this.$emit('products', this.inputData )
        },

        clearData: function () {
            this.inputData = "";
            this.$emit('products', this.inputData );
        }
    }
}
</script>