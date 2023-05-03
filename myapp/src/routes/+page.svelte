<script>
    import Campaigning from "../components/campaigning.svelte";
let state = {
    clout: 0,
    money: 100,
    people: 0,
    doors: 0,
    peopleCost: 10,
}





</script>


<h1>Political Simulator</h1>

<Campaigning bind:state={state} />
