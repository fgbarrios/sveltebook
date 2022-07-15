<script>
  import {products, cart} from "../stores.js";
  import Cart from "./Cart.svelte";  

  //export let location;
  
  const addToCart = (product) => {
    for (let item of $cart) {
        if(item.id === product.id) {
          product.quantity += 1
          $cart = $cart;
          return;
        }
    }
    $cart = [...$cart, product]
  }
</script>

<style>
/* Agregar despues */ 
</style>


<div class="product-list">
  {#each $products as product}
    <div>
      <div class="image" style="background-image: url({product.image})"></div>
      <h4><a href="product/{product.id}">{product.name}</a></h4>
      <div class="cta">
        <p>${product.price}</p>
        <button on:click={() => addToCart(product)}>Agregar al carrito</button>
      </div>
    </div>
  {/each}
</div>

<Cart />