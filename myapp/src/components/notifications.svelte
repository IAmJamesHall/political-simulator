<script>
    import  { fade } from 'svelte/transition';
    export let state;

    // remove any notifications from array that have been in state for more than 5 seconds
    const removeOldNotifications = () => {
        state.notifications = state.notifications.filter(n => {
            const now = new Date();
            const diff = now - n.date;
            return diff < 2000;
        });
    }


    // run removeOldNotifications every second
    setInterval(removeOldNotifications, 1000);

</script>

<div id="notifications">
    {#each [...state.notifications].reverse() as n}
        <p out:fade="{{ duration: 2000}}">{n.message}</p>
    {/each}
</div>

<style>
    #notifications {
        position: fixed;
        top: 0;
        right: 0;
        width: 200px;
        height: 100%;
        /* background-color: #eee; */
        padding: 10px;
        overflow-y: scroll;
    }

    p {
        border: 1px solid #ccc;
        padding: 10px;
        margin: 10px 0;
    }
</style>