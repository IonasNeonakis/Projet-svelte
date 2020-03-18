<script>
    export let variable="";
    export let placeholdervariable;
    export let labelvariable="variable";
    let classButoon="";

    


    export let verifierLongueur;
    function verifier(){
        if(verifierLongueur(variable)){
            classButoon="is-valid";
        }else{
            classButoon="is-invalid";
        }
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
<input id="inputnom" bind:value={variable}  on:keyup={verifetChangement} class="form-control {classButoon}"  placeholder="{placeholdervariable}">
<div class="invalid-feedback">La longueur doit etre au moins de 2</div>
</div>