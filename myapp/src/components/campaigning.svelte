<script>
    export let state = {};

    const hireSomeone = () => {
        if (state.money >= state.peopleCost) {
            state.people += 1;
            state.money -= state.peopleCost;
        } else {
            alert("You don't have enough money to hire someone.");
        }
    }

    const recruitFriend = () => {
        const chance = Math.random();
        if (chance > 0.5) {
            state.people += 1;
        } else {
            state.notifications.push("Your friend doesn't want to help you.");
        }
    }

const updateVars = () =>{
    state.doors += state.people;
    state.clout += Math.round(state.people * (Math.random() * 0.1));
}

// run updateVars every second
setInterval(updateVars, 1000);


// for every person, generate a random number between 0.2 and 0.3 and multiply people by that to get clout. Round to nearest integer

</script>

<h3>Campaigning</h3>
<p>Talk to people in your town to gain clout.<br>

<!-- button to talk to people -->
<button on:click={() => state.doors += 1}>Knock on a door</button><br>
<b>Doors: {state.doors}</b>
</p>

{#if state.doors > 10}
<p>Ask a friend to help you.<br>
<button on:click={recruitFriend}>Recruit a friend</button></p>
{/if}

{#if state.money}
<p>Hire someone to knock on doors for you.<br>
<button on:click={hireSomeone}>Hire someone</button><br>
<b>Door-knockers: {state.people}</b></p>
{/if}



<p>Money: {state.money}</p>
<p>Clout: {state.clout}</p>


{#if state.doors > 1000}

{/if}