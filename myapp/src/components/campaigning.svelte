<script>
    export let state = {};

    const hireSomeone = () => {
        state.achievements.doorKnockers = true;
        if (state.money >= state.peopleCost) {
            state.people += 1;
            state.money -= state.peopleCost;
        } else {
            state.addNotification("You don't have enough money to hire someone.");
        }
    };

    const recruitFriend = () => {
        const chance = Math.random();
        if (chance > 0.5) {
            state.people += 1;
            state.addNotification("Yay! Your friend has joined your cause.");
        } else {
            state.addNotification("Boo. Your friend doesn't want to help you");
        }
    };

    const askForDonations = () => {
        const donationRate = Math.random() / 10;
        const donations = Math.round(donationRate * state.supporters);
        state.money += donations;

        const supporterLossRate = Math.random() / 10;
        const supportersLost = Math.round(
            supporterLossRate * state.supporters
        );
        state.supporters -= supportersLost;

        const reasonsForLoss = [
            "you were too pushy.",
            "you were too aggressive.",
            "you were too needy.",
            "you were too demanding.",
            "you were too annoying.",
            "you were too loud.",
            "you looked sketchy.",
            "you were a salesman",
            "you were their grandmother.",
            "your campaign was too vague.",
        ];

        //pick random element from array
        const reason =
            reasonsForLoss[Math.floor(Math.random() * reasonsForLoss.length)];

        state.addNotification(`You received $${donations} in donations, and lost ${supportersLost} supporters who thought ${reason}`);
    }

    const updateVars = () => {
        state.doors += state.people;
        state.supporters += Math.round(state.people * (Math.random() * 0.1));
    };

    // run updateVars every second
    setInterval(updateVars, 1000);

    // for every person, generate a random number between 0.2 and 0.3 and multiply people by that to get clout. Round to nearest integer
</script>

<h3>Campaigning</h3>
<i>Goal: Gain supporters for your future aspirations</i><br>
<b>Supporters: {state.supporters}</b>
<hr>

    <!-- button to talk to people -->
    <button on:click={() => (state.doors += 1)}>Knock on door</button><br />
    <b>Doors: {state.doors}</b>

{#if state.doors >= 10}
    <p>
        Try to recruit a friend to knock too
        <button on:click={recruitFriend}>Ask</button><br>
        {#if state.money > 100 || state.achievements.doorKnockers}
            Hire someone to knock on doors for you.
            <button on:click={hireSomeone}>costs $10</button><br>
        {/if}
        <b>Door-knockers: {state.people}</b> ({state.people} doors/s)
    </p>
{/if}


{#if state.supporters > 100}
    <p>Ask your supporters for money
    <button on:click={askForDonations}>Send request</button><br />
    <b>Money: ${state.money}</b></p>
{/if}
