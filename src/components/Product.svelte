<script>
  import {products, cart} from "../stores.js";
  //import Button from "./Button.svelte";
  
  let individualID = document.location.pathname.split("/")[2];
  let individualName;
  
  const addToCart = (product) => {
    for(let item of $cart) {
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


<a href="/products">{"<< Volver a la tienda"}</a>

<div id="productdetails">
  {#each $products as product }
    {#if product.id == individualID}
      <div>
        <p><img src="{product.large_image}" alt="{product.name}" /></p>
      </div>
      <div>
        <p>{product.name}</p>
        <p>SKU: {individualID}</p>
        <p>{product.description}</p>
        <h2>${product.price}</h2>
        <button on:click={() => addToCart(product)}>Agregar al carrito</button>
      </div>
    {/if}
  {/each}
</div>

