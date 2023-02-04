<script>
   import Button from "./Button.svelte";
   import { link } from "svelte-spa-router";
   import { cart } from "./store/store.js";

   let cartList;
   let unsub = cart.subscribe((value) => {
      cartList = value;
   });

   $: sumPrice = countSumPrice(cartList);

   function countSumPrice(array) {
      let price = 0;

      array.forEach((element) => {
         price += element.price * element.count;
      });

      return price;
   }
</script>

<header>
   <div class="container">
      <div class="logo">
         <div class="img">
            <img src="/img/logo.png" alt="X" />
         </div>
         <div class="text">
            <div class="name">Svelte Pizza</div>
            <div class="description">сама смачна піца</div>
         </div>
      </div>
      <div class="card-button">
         <a
            href="/cart"
            class="btn orange"
            style="text-decoration: none;"
            use:link
         >
            <span><b>$</b>{sumPrice}</span> | <span>{cartList.length}</span>
         </a>
      </div>
   </div>
</header>
