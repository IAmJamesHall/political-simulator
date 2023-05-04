<script>
    import Campaigning from "../components/campaigning.svelte";
    import Notifications from "../components/notifications.svelte";

    let state = {
        supporters: 0,
        money: 100,
        people: 0,
        doors: 0,
        peopleCost: 10,
        notifications: [],
        isSave: false,
    };

    // if (!state.isSave) {
    //     if (localStorage.getItem("state")) {
    //         state = JSON.parse(localStorage.getItem("state"));
    //     }
    // }
</script>

<h1>Political Simulator</h1>

<Campaigning bind:state />
<Notifications bind:state />
