<script>
    import Campaigning from "../components/campaigning.svelte";
    import Notifications from "../components/notifications.svelte";
let state = {
    clout: 0,
    money: 100,
    people: 0,
    doors: 0,
    peopleCost: 10,
    notifications: [],
}





</script>


<h1>Political Simulator</h1>

<Campaigning bind:state={state} />
<Notifications bind:state={state} />
