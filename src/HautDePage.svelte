<script>
	export let name="";
    export let namecorrect;

    
    export let placeholdernom;
    export let labelnom="Nom";

    export let verifierLongueur;
    

    function verifierlon(names){
        namecorrect=verifierLongueur(name);
    }

</script>

<svelte:head>
	<link rel="stylesheet" href="bootstrap.min.css">
</svelte:head>

<main>
	<h1>Bonjour {name}!</h1>
</main>

<div class="form-group">
<label class="form-control-label" for="inputnom" id="nomLabel">{labelnom}</label>
<input id="inputnom" bind:value={name} on:keyup={verifierlon(name)} class="form-control {namecorrect ? 'is-valid' : 'is-invalid' }"  placeholder="{placeholdernom}">
<div class="invalid-feedback">La longueur doit etre au moins de 2</div>
</div>
