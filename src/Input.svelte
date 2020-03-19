<script>
    export let variable="";
    export let placeholdervariable="";
    export let labelvariable="variable";
    export let variableValide=false;
    export let messageErreur="Erreur"

    let classinput="";

    export let verifierLongueur;

    function verifier(){
        if(verifierLongueur(variable)){
            variableValide=true;
            classinput="is-valid";
        }else{
            variableValide=false;
            classinput="is-invalid";
        }
    }


</script>

<svelte:head>
	<link rel="stylesheet" href="bootstrap.min.css">
</svelte:head>


<div class="form-group">
<label class="form-control-label" for="inputnom" id="nomLabel">{labelvariable}</label>
<input id="inputnom" bind:value={variable}  on:keyup={verifier} class="form-control {classinput}"  placeholder="{placeholdervariable}">
<div class="invalid-feedback">{messageErreur}</div>
</div>