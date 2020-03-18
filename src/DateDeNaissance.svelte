<script> 

    import Datepicker from 'svelte-calendar';
    import { formatDate } from 'timeUtils';

    const minDate= new Date(1899,12,1);
    const maxDate= new Date();

    let selectedDate= new Date();

    let age=maxDate.getFullYear() - selectedDate.getFullYear();


    const affichageDateSelected="Choisir date d'anniversaire";

    let affichageDateUnselected="Né le #{j} #{F} #{Y} ("+age+" ans)";

    let userHasChosenDate;

    function getAge(){
        age=maxDate.getFullYear() - selectedDate.getFullYear();
        affichageDateUnselected="Né le #{j} #{F} #{Y} ("+age+" ans)";
    }

    console.log(maxDate.getFullYear())
    console.log(selectedDate.getFullYear())
    

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