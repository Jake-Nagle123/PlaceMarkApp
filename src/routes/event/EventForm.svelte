<script lang="ts">
import Coordinates from "$lib/ui/Coordinates.svelte";

  const stadiumList = [
    {
     ground: "Aviva Stadium",
    },
    {
      ground: "Croke Park",
    },
    {
      ground: "Fraher Field",
    },
    {
     ground: "Páirc Uí Chaoimh",
    },
    {
      ground: "Thomond Park",
    },
    {
      ground: "Walsh Park",
    },
    {
      ground: "Other",
    }
  ];

  let amount = $state(0);
  let selectedStadium = $state("Walsh Park");
  let sportMethods = ["Hurling", "Football", "Soccer", "Rugby"];
  let selectedSport = $state("Hurling");
  let city = $state(""); 
  let latitude = $state(52.160858);
  let longitude = $state(-7.15242);


  async function addEvent() {
    console.log(`Just added: ${selectedStadium} to ${sportMethods} which cost ${amount}`);
    console.log(`lat: ${latitude}, lng: ${longitude}`);
  }
</script>

<div>
  <div class="field">
    <label class="label" for="amount">Enter Ticket Price:</label>
    <input bind:value={amount} class="input" id="amount" name="amount" type="number" />
  </div>

  <div class="field">
    <label class="label" for="city">Enter County:</label>
    <input bind:value={city} class="input" id="city" name="city" type="text" />
  </div>

  <div class="field">
    <div class="control">
      <label class="label" for="sport">Select Sport:</label>
      {#each sportMethods as method}
        <input bind:group={selectedSport} class="radio" type="radio" value={method} /> {method}
      {/each}
    </div>
  </div>

  <div class="field">
    <label class="label" for="rating">Enter Rating:</label>
    <input class="input" id="rating" name="rating" type="float" />
  </div>

  <div class="field">
    <label class="label" for="stadium">Select County:</label>
    <div class="select">
      <select bind:value={selectedStadium}>
        {#each stadiumList as stadium}
          <option>{stadium.ground}</option>
        {/each}
      </select>
    </div>
  </div>
  <Coordinates bind:latitude bind:longitude />
  <div class="field">
    <div class="control">
      <button onclick={() => addEvent()} class="button is-success is-fullwidth">Submit</button>
    </div>
  </div>
</div>