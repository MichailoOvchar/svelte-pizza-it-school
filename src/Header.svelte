<script>
   import Button from "./Button.svelte";
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
         <Button>
            <span><b>$</b>000</span>
         </Button>
      </div>
   </div>
</header>
