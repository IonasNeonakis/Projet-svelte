<script>
	import Input from './Input.svelte';
	import DateDeNaissance from './DateDeNaissance.svelte'


	let nom = "";
	let prenom = "";
	let numero;
	let dateNaissance;

	let nomValide;
	let prenomValide;
	let numValide;
	let dateValide;


	const regTel =/^([0-9][0-9] ?){5}$/ ; 
	function telValidator(string){
		return regTel.test(string);
	}

	function veriflongueur2(name){
		if (name.length<2)
			return false;
		else
			return true;
	};

	let tabPersonnes=[];

	function creerPersonne(){
		if( nomValide && dateValide && prenomValide && numValide){
			let personne ={
				nom : nom,
				prenom : prenom,
				numero : numero,
				dateNaissance : dateNaissance
			}
			tabPersonnes = [...tabPersonnes, personne]
			console.log(tabPersonnes)
		}
	}

	function getAge(date) {
		let datefinale = date.getDate() + "/" + ((date.getMonth())+1) + "/" + date.getFullYear();
		return datefinale;
	}


</script>

<h1>Bonjour {prenom + " " +nom}</h1>


<Input placeholdervariable={"Entrez un nom"}
		labelvariable={"Nom"}
		messageErreur={"La longueur doit être au moins de 2"}
		bind:variableValide={nomValide}
		bind:variable={nom}
		verifierLongueur={veriflongueur2}
	/>

<Input placeholdervariable={"Entrez un prenom"}
		labelvariable={"Prenom"}
		messageErreur={"La longueur doit être au moins de 2"}
		bind:variableValide={prenomValide}
		verifierLongueur={veriflongueur2}
		bind:variable={prenom}
	/>

<Input placeholdervariable={"Entrez un numero de Téléphone"}
		labelvariable={"N° téléphone"}
		messageErreur={"Entrez un numéro de téléphone valide"}
		bind:variableValide={numValide}
		verifierLongueur={telValidator} 
		bind:variable={numero}

	/>

<DateDeNaissance bind:userHasChosenDate={dateValide}
		bind:dateNaissance={dateNaissance}
	/>

<button on:click={creerPersonne}  
		class="btn"
		class:btn-warning="{ !nomValide || !dateValide || !prenomValide || !numValide}"
		class:disabled="{!nomValide || !dateValide || !prenomValide || !numValide}"
		class:btn-success="{ nomValide && dateValide && prenomValide && numValide}"
	>Créer</button>

<table class="table table-hover">
					<thead>
						<tr>
							<th>
								Prénom
							</th>
							<th>
								Nom
							</th>
							<th>
								Téléphone
							</th>
							<th>
								Date de naissance
							</th>
						</tr>
					</thead>
					<tbody>
						{#each tabPersonnes as person}
							<tr>
								<td>
									{person.nom}
								</td>
								<td>
									{person.prenom}
								</td>
								<td>
									{person.numero}
								</td>
								<td>
									{getAge(person.dateNaissance)}
								</td>
							</tr>
						{/each}
					</tbody>
				</table>