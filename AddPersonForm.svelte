<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();
  let name;
  let beltColour;
  let age;
  // let fighting = false;
  // let sneaking = false;
  // let running = false;
  let skills = [];

  const handleSubmit = () => {
    const person = {
      name: name,
      beltColour: beltColour,
      age: age,
      skills: skills,
      id: Math.random()
    };
    dispatch("addPerson", person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
<div class="input">
    <input type="text" placeholder="name" bind:value={name}>
    <!-- <input type="text" placeholder="belt colour" bind:value={beltColour}> -->
    <input type="number" placeholder="age" bind:value={age}><br>
</div>
    <div class="checkbox">
        <label >Skills:</label><br>
        <!-- <input type="checkbox" bind:checked={fighting}>fighting<br>
        <input type="checkbox" bind:checked={sneaking}>sneaking<br>
        <input type="checkbox" bind:checked={running}>running<br> -->
        
        <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
        <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
        <input type="checkbox" bind:group={skills} value="running">running<br>
    </div>
    <div class="select">
        <label >Belt Colour:</label><br>
        <select bind:value={beltColour}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="brown">brown</option>
        <option value="white">white</option>
        </select>
    </div>
    <button>Add Person</button>
</form>

<style>
form {
  margin-top: 20px;
  margin-left: 20px;
}
.checkbox , .select {
  padding: 5px;
  font-size: 1.2rem;
}
.checkbox , .select{
  margin-top: 10px;
  text-align: left;
}
.input  {
  text-align: left;
}
.input > input {
  border: 1.5px solid black;
  border-radius: 5px;
  padding: 0 5px;
  font-size: 1.2rem;
  width: 150px;
}
input[type="number"] {
  width: 50px;
}
button {
  border-radius: 5px;
  font-size: 1.2rem;
  cursor :pointer;
}
</style>