<script>
	import Input from './Input.svelte';
	import DateDeNaissance from './DateDeNaissance.svelte'

	const regTel =/^([0-9][0-9] ?){5}$/ ; 

	let prenompapa="";

	function modifprenompapa(string){
		prenompapa=string;
	}

	function telValidator(string){
		return regTel.test(string);
	}


	function veriflongueur2(name){
		if (name.length<2)
			return false;
		else
			return true;
		
	};

</script>

<h1>Bonjour {prenompapa}</h1>


<Input placeholdervariable={"Entrez un nom"} labelvariable={"Nom"} verifierLongueur={veriflongueur2} modifTitle={modifprenompapa}/>

<Input placeholdervariable={"Entrez un prenom"} labelvariable={"Prenom"} verifierLongueur={veriflongueur2} />

<Input placeholdervariable={"Entrez un numero de Téléphone"} labelvariable={"N° téléphone"} verifierLongueur={telValidator} />

<DateDeNaissance/>