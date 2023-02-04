<script>
   import { link } from "svelte-spa-router";
   import { onDestroy } from "svelte";
   import CartComponent from "../CartComponent.svelte";
   import { cart } from "../store/store.js";

   let cartList;
   let unsub = cart.subscribe((value) => {
      cartList = value;
   });

   function updatePizzaCart(name, size, count) {
      if (count > 0) {
         let index = cartList.findIndex(
            (fn) => fn.name == name && fn.size == size
         );

         if (index >= 0) {
            cartList[index].count = count;
            cart.set([...cartList]);
         }
      } else {
         let newArray = cartList.filter(
            (fn) => fn.name != name && fn.size != size
         );
         cart.set(newArray);
      }

      localStorage.setItem("pizzaCart", JSON.stringify(cartList));
   }

   onDestroy(unsub);
</script>

<section id="cart">
   {#if cartList.length > 0}
      <div class="container list">
         <div class="header">
            <div class="title">
               <i class="fa-solid fa-cart-shopping" /> Корзина товарів
            </div>
            <div class="delete-all">
               <i class="fa-solid fa-trash" /> видалити з корзини
            </div>
         </div>
         <div class="list">
            {#each cartList as pizza (pizza.name + pizza.size)}
               <CartComponent
                  name={pizza.name}
                  size={pizza.size}
                  startPrice={pizza.price}
                  number={pizza.count}
                  img={pizza.img}
                  on:change={(e) => {
                     updatePizzaCart(pizza.name, pizza.size, e.detail.count);
                  }}
                  on:delete={() => {
                     updatePizzaCart(pizza.name, pizza.size, 0);
                  }}
               />
            {/each}
         </div>
         <div class="button">
            <a href="/" class="btn black" use:link>Переглянути меню</a>
            <button class="btn orange"> Оплатити замовлення </button>
         </div>
      </div>
   {:else}
      <div class="container">
         <div class="title">Корзина пуста 😕</div>
         <div class="description">Скоріше всього Ви ще не обрали піцу</div>
         <div class="image">
            <img src="/img/shopping-cart-colour.svg" alt="Empty cart" />
         </div>
         <div class="button">
            <a href="/" class="btn black" use:link> Вибрати піцу </a>
         </div>
      </div>
   {/if}
</section>
