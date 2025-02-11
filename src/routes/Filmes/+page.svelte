<script>
    import { filmes, gêneros } from '$lib/filmes.js';
  
    let gênerosSelecionados = $state([]);
    let filtrados = $state(filmes.slice());
  
    function filtrarGenero(event) {
        if (event.target.checked) {
            gênerosSelecionados.push(event.target.value);
        } else {
            gênerosSelecionados.splice(gênerosSelecionados.indexOf(event.target.value), 1);
        }
  
        if (gênerosSelecionados.length == 0) {
            filtrados = filmes.slice();
        } else {
            filtrados = [];
            for (const filme of filmes) {
                for (const gênero of gênerosSelecionados) {
                    if (filme.gêneros.includes(gênero)) {
                        filtrados.push(filme);
                        break;
                    }
                }
            }
        }
    }
  </script>
  
  <div class="row align-items-center mb-3">
    <div class="col-md-4"><input class="form-control" placeholder="Filtrar..." /></div>
    {#each gêneros as gênero}
        <div class="col">
            <div class="form-check form-check-inline">
                <input type="checkbox" oninput={filtrarGenero} class="form-check-input" id={gênero} value={gênero} />
                <label class="form-check-label" for={gênero}>{gênero}</label>
            </div>
        </div>
    {/each}
  </div>
  <div class="row g-4">
    {#each filtrados as filme}
        <div class="col-md-6 col-xl-3">
            <div class="card h-100">
                <div class="row g-0">
                    <div class="col-3 col-sm-4">
                        <img src={filme.imagem} class="img-fluid rounded-start" alt="capa do filme" />
                    </div>
                    <div class="col-sm-8">
                        <div class="card-body">
                            <h5 class="card-title">{filme.título}</h5>
                            <h6 class="card-subtitle mb-2 text-body-secondary">{filme.ano}</h6>
                            <p class="card-text">{filme.sinopse}</p>
                            <p class="card-text">
                                {#each filme.gêneros as gênero}
                                    <span class="badge text-bg-secondary mx-1">{gênero}</span>
                                {/each}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    {/each}
  </div>