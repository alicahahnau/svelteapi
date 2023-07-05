<script>
  import { onMount } from "svelte";
  import { navigate } from "svelte-routing";
  

  export let selectCocktail;
  let cocktails = [];

  onMount(async () => {
    const response = await fetch(
      "https://www.thecocktaildb.com/api/json/v1/1/search.php?s="
    );
    const data = await response.json();
    cocktails = data.drinks || [];
  });

  function handleClick(cocktail) {
    selectCocktail(cocktail);
    navigate(`/cocktail/${cocktail.idDrink}`);
  }

  function handleKeyDown(event, cocktail) {
    if (event.key === "Enter") {
      handleClick(cocktail);
    }
  }
</script>

<main>
  <h2>Search Results:</h2>
  {#if cocktails.length > 0}
    <ul>
      {#each cocktails as cocktail}
        <div
          class="cocktail-item"
          role="button"
          tabindex="0"
          on:click={() => navigate(`/cocktail/${cocktail.idDrink}`)}
          on:keydown={(event) => {
            if (event.key === "Enter") {
              navigate(`/cocktail/${cocktail.idDrink}`);
            }
          }}
        >
          <h3>{cocktail.strDrink}</h3>
          <img src={cocktail.strDrinkThumb} alt={cocktail.strDrink} />
        </div>
      {/each}
    </ul>
  {:else}
    <p>Loading...</p>
  {/if}
</main>

<style>
  main {
    text-align: center;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    cursor: pointer;
    padding: 8px;
    margin-bottom: 4px;
    background-color: #f0f0f0;
    border-radius: 4px;
  }

  li:focus {
    outline: none;
    background-color: #ddd;
  }

  .cocktail-item {
    width: 20%;
    height: 20%;
  }
</style>
