<script>
   import { createEventDispatcher } from "svelte";

   export let name = "";
   export let size = "0";
   export let number = 0;
   export let img = "/img/pizza.jpg";

   export let startPrice = 100;

   let dispatcher = createEventDispatcher();

   $: countPrice = startPrice * number;
</script>

<div class="item cart">
   <div class="image">
      <img src={img} alt="X" />
   </div>
   <div class="info">
      <div class="name">{name}</div>
      <div class="type">{size} cm.</div>
   </div>
   <div class="number">
      <div
         class="button"
         on:click={() => {
            number--;
            dispatcher("change", {
               count: number,
            });
         }}
      >
         -
      </div>
      <div class="count">{number}</div>
      <div
         class="button"
         on:click={() => {
            number++;
            dispatcher("change", {
               count: number,
            });
         }}
      >
         +
      </div>
   </div>
   <div class="price">{countPrice} грн.</div>
   <div
      class="delete"
      on:click={() => {
         dispatcher("delete");
      }}
   >
      &times;
   </div>
</div>
