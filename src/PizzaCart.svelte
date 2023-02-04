<script>
   import { onMount } from "svelte";
   import { cart } from "./store/store.js";
   import PizzaSizeSelector from "./PizzaSizeSelector.svelte";
   import { onDestroy } from "svelte";

   export let imageUrl = "";
   export let name = "Pizza";
   export let price = 100;

   export let sizes = [];

   let selectSize = "1";

   let formatedSize = [];

   let cartList;
   let unsub = cart.subscribe((value) => {
      cartList = value;
   });

   function buyPizza() {
      let newPizza = {
         name: name,
         img: imageUrl,
         price: price,
         count: 1,
         size: selectSize,
      };

      let findPizza = cartList.findIndex(
         (fn) => fn.name == name && fn.size == selectSize
      );

      if (findPizza >= 0) {
         cartList[findPizza].count++;
         cart.set([...cartList]);
      } else {
         cart.set([...cartList, newPizza]);
      }

      localStorage.setItem("pizzaCart", JSON.stringify(cartList));
   }

   onMount(function () {
      if (typeof sizes[0] == "object") {
         formatedSize = sizes;
      } else {
         formatedSize = sizes.map((fn) => {
            return {
               name: fn,
               value: fn,
            };
         });
      }
   });

   onDestroy(unsub);
</script>

<div class="pizza-cart">
   <div class="img">
      <img src={imageUrl} alt="X" />
   </div>
   <div class="name">{name}</div>

   {#if formatedSize.length > 0}
      <PizzaSizeSelector size={formatedSize} bind:selectedValue={selectSize} />
   {/if}

   <div class="price-block">
      <div class="price">від {price} грн</div>
      <div class="button" on:click={buyPizza}>
         <div class="btn orange">Купити</div>
      </div>
   </div>
</div>
