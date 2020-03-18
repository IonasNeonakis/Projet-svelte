<script>
    //variable
    export let variable="";
    export let variableCorrect;
    export let placeholdervariable;
    export let labelvariable="variable";


    export let verifierLongueur;
    function verifier(){
        variableCorrect=verifierLongueur(variable);
    }

    export let modifTitle;

    function changerTitre(){
        modifTitle(variable);
    }

    function verifetChangement(){
        verifier();
        changerTitre(variable);
    }


</script>

<svelte:head>
	<link rel="stylesheet" href="bootstrap.min.css">
</svelte:head>


<div class="form-group">
<label class="form-control-label" for="inputnom" id="nomLabel">{labelvariable}</label>
<input id="inputnom" bind:value={variable}  on:keyup={verifetChangement} class="form-control {variableCorrect ? 'is-valid' : 'is-invalid' }"  placeholder="{placeholdervariable}">
<div class="invalid-feedback">La longueur doit etre au moins de 2</div>
</div>


