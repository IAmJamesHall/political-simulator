
<script>
    //TODO: implement localstorage save/load
    import Campaigning from "../components/campaigning.svelte";
    import Notifications from "../components/notifications.svelte";

    let state = {
        supporters: 100,
        money: 0,
        people: 100,
        doors: 1000,
        peopleCost: 10,
        addNotification: (message) => {
            state.notifications.push({ date: new Date(), message })
        },
        notifications: [],
        isSave: false,
        achievements: {
            doorKnockers: false,
        }
    };

</script>

<h1>Just a Friendly Game</h1>

<Campaigning bind:state />
<Notifications bind:state />
