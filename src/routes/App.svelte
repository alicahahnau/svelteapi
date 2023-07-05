<!--
	



	============================================================
	
	kp was diese datei hier machen soll. das brauchen wir nicht. 

	============================================================




-->

<!-- <script>
        import { Router, Link, Route } from 'svelte-routing';
        import Home from './+page.svelte';
        import CocktailDetails from '$lib/components/CocktailDetails.svelte';

        let selectedCocktail = null;

        function selectCocktail(cocktail) {
                selectedCocktail = cocktail;
        }
</script>

<main>
        <h1>Cocktail Search</h1>
        <Router>
                <nav>
                        <Link to="/">Home</Link>
                </nav>

                <div>
                        <Route path="/" component={Home} props={{ selectCocktail }} />
                        {#if selectedCocktail}
                                <Route path="/cocktail/:id" let:routeProps>
                                        <CocktailDetails cocktailId={routeProps.params.id} />
                                </Route>
                        {/if}
                </div>
        </Router>
</main>

<style>
        main {
                text-align: center;
        }

        nav {
                margin-bottom: 20px;
        }

        a {
                margin-right: 10px;
        }
</style> -->
