<script>
   import PizzaSizeSelector from "./PizzaSizeSelector.svelte";

   export let image = "";
   export let name = "Pizza";
   export let price = 100;

   export let size = [];
</script>

<div class="pizza-cart">
   <div class="img">
      <img src={image} alt="X" />
   </div>
   <div class="name">{name}</div>

   <PizzaSizeSelector size={size} />

   <div class="price-block">
      <div class="price">від {price} грн</div>
      <div class="button">
         <div class="btn orange">Купити</div>
      </div>
   </div>
</div>
