<script>
    import Cartasdoce from '$lib/components/Cartasdoce.svelte';
    import { cards } from '$lib/perfumes.js';
  </script>
   
  <div class="row g-4">
    {#each cards as card}
      <div class="col">
        <Cartasdoce {...card} />
      </div>
    {/each}
  </div>