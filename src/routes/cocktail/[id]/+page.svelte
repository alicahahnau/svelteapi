<script>
        import { page } from '$app/stores';
        import { onMount } from 'svelte';
        let cocktailId = 0;

        onMount(() => {
                cocktailId = $page.params.id;
        });
</script>

<h1>Das ist eine Unterseite für den Coktail mit der id: {cocktailId}</h1>
