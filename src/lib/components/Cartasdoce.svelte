<script>
    let { img, title,  text } = $props();
  </script>
   
  <div class="card h-100" style="width: 18rem;">
    <img src={img} class="card-img-top" alt="invisibility" width="500px" />
    <div class="card-body">
      <h1 class="card-title">{title}</h1>
      <p class="card-text">{text}</p>
    </div>
  </div>

