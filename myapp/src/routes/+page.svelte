<script>
let vars = {
    clout: 0,
    money: 0,
    people: 0,
    doors: 0,
    peopleCost: 10,
}

const updateVars = () =>{
    vars.doors += vars.people;
}

// run updateVars every second
setInterval(updateVars, 1000);

const hireSomeone = () => {
    if (vars.money >= vars.peopleCost) {
        vars.people += 1;
        vars.money -= vars.peopleCost;
    } else {
        alert("You don't have enough money to hire someone.");
    }
}
</script>


<h1>Political Simulator</h1>
<p>Talk to people in your town to gain clout.</p>
//button to talk to people
<button on:click={() => vars.doors += 1}>Knock on doors</button>

<p>Hire someone to knock on doors for you.</p>
<button on:click={hireSomeone}>Hire someone</button>

<p>Doors: {vars.doors}</p>