<script>
    import { onMount } from 'svelte';
    import { useParams } from 'svelte-routing';
    import { Route } from 'svelte-spa-router';
  
    let cocktail = null;
  
    const { id } = useParams();
  
    onMount(async () => {
      try {
        const response = await fetch(`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${id}`);
        const data = await response.json();
        cocktail = data.drinks[0];
      } catch (error) {
        console.error(error);
      }
    });
  </script>
  
  <main>
    <h2>Details:</h2>
    {#if cocktail}
      <h3>{cocktail.strDrink}</h3>
      <img src={cocktail.strDrinkThumb} alt={cocktail.strDrink} />
      <p>{cocktail.strInstructions}</p>
    {:else}
      <p>Loading...</p>
    {/if}
  </main>
  
  <style>
    main {
      text-align: center;
    }
  
    img {
      max-width: 300px;
      margin: 20px auto;
    }
  </style>
  