<script>
	import HautDePage from './HautDePage.svelte';


	function verif(name){
		if (name.length<2){
			return false;
		}else{
			return true;
		}
	};

</script>



<HautDePage placeholdernom={"Entrez un nom"} labelnom={"Nom"} verifierLongueur={verif}/>
