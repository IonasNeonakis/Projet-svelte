<script> 

    import Datepicker from 'svelte-calendar';
    import { formatDate } from 'timeUtils';

    const minDate = new Date(1899,12,1);
    const maxDate = new Date();


    export let dateNaissance=new Date();
    export let userHasChosenDate=false;


    let selectedDate;
    
    let age;




    const affichageDateSelected = "Choisir date d'anniversaire";

    let affichageDateUnselected = "Né le #{j} #{F} #{Y} (" + age + " ans)";


    function getAge(){
        let today = new Date();
	    age = today.getFullYear() - selectedDate.getFullYear();
	    let m = today.getMonth() - selectedDate.getMonth();
	    if (m < 0 || (m === 0 && today.getDate() < selectedDate.getDate())) {
		    age = age - 1;
        }
        dateNaissance = selectedDate;
        affichageDateUnselected = "Né le #{j} #{F} #{Y} (" + age + " ans)";
    }


    const daysOfWeek = [
        ['Dimanche', 'Dim'],
        ['Lundi', 'Lun'],
        ['Mardi', 'Mar'],
        ['Mercredi', 'Mer'],
        ['Jeudi', 'Jeu'],
        ['Vendredi', 'Ven'],
        ['Samedi', 'Sam']
        ];

    const monthsOfYear = [
        ['Janvier', 'Jan'],
        ['Fevrier', 'Fev'],
        ['Mars', 'Mar'],
        ['Avril', 'Avr'],
        ['Mai', 'Mai'],
        ['Juin', 'Jui'],
        ['Juiller', 'Jui'],
        ['Août', 'Aoû'],
        ['Septembre', 'Sep'],
        ['Octobre', 'Oct'],
        ['Novembre', 'Nov'],
        ['Decembre', 'Dec']
        ];



</script>


<div class="form-group">
<Datepicker  start={minDate}   bind:selected={selectedDate} daysOfWeek={daysOfWeek} bind:dateChosen={userHasChosenDate} format={date => {
    
    if(!userHasChosenDate){
        return formatDate(date,affichageDateSelected);
    }else{
                getAge();

        return formatDate(date,affichageDateUnselected);
    }

}}  monthsOfYear={monthsOfYear} end={maxDate}/>

</div>