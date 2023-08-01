<template>
    <div>
        <h1>Products</h1>
    </div>
    <div>
        <div class="card" style="margin: 5px; padding: 10px">
        <h2>Product 1</h2>
        <p>Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet
        </p>
        <button @click="addToCart(1)">Add to cart</button>
        </div>
        <div class="card">
                <h2>Product 2</h2>
                <p>
                        Lorem ipsum dolor sit amet Lorem ipsum dolor sit ametLorem ipsum dolor sit amet</p>
                <button @click="addToCart(2)">
                Add to cart
                </button>
        </div>
        <div class="card" style="margin: 5px; padding: 10px">


            <h3>Product 3</h3>
            <p>Lorem ipsum dolor sit amet</p>
            <button @click="addToCart(3)">Add to cart</button>
        </div>
        <div class="card" style="margin: 5px; padding: 10px;">
            <h2>Product 4</h2>
            <p>Lorem ipsum dolor sit amet</p>
            <button @click="addToCart(4)">Add to cart</button>
        </div>
        <div 
        class="card" 
        style="margin: 5px; padding: 10px;">
        <h2>Cart</h2>
            <p v-if="cart.length === 0">Cart is empty</p>
            <ul v-else>
                <li v-for="item in cart">
            {{ item.name }}-{{ item.price }}
                </li>
            </ul>
        </div>
        <div style="font-weight: 600; margin-left: auto; margin-right: auto; font-size: 32px; outline: 1px solid black;">
        <p>Total price: {{ cart.reduce((total, product) => total + product.price, 0) }}</p>
        </div>
        <button @click="purchase()" id="purchaseButton">Purchase</button>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            cart: []
        }
    },
    methods: {
        addToCart(productId) {
            if (productId === 1) {
                this.cart.push({ name: 'Product 1', price: 10 })
            } else if (productId === 2) {
                this.cart.push({ name: 'Product 2', price: 20 })
            } else if (productId === 3) {
                this.cart.push({ name: 'Product 3', price: 30 })
            } else if (productId === 4) {
                this.cart.push({ name: 'Product 4', price: 40 })
            }
        },
        purchase() {
            this.$emit('purchase', this.cart)
        }
    },
    props: ['username']
}
</script>
  
<style>
.card {
border: 1px solid black;
padding: 1rem;
margin: 1rem;
width: 300px;
background-color: white;
color: black;
}

#purchaseButton {
margin-left: auto;
margin-right: auto;
display: block;
font-size: 32px;
background-color: blue;
color: black;
}
</style>