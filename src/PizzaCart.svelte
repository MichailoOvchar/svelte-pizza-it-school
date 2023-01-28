<script>
   import { onMount } from "svelte";
   import PizzaSizeSelector from "./PizzaSizeSelector.svelte";

   export let imageUrl = "";
   export let name = "Pizza";
   export let price = 100;

   export let sizes = [];

   let formatedSize = [];

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
</script>

<div class="pizza-cart">
   <div class="img">
      <img src={imageUrl} alt="X" />
   </div>
   <div class="name">{name}</div>

   {#if formatedSize.length > 0}
      <PizzaSizeSelector size={formatedSize} />
   {/if}

   <div class="price-block">
      <div class="price">від {price} грн</div>
      <div class="button">
         <div class="btn orange">Купити</div>
      </div>
   </div>
</div>
