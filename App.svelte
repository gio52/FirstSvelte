<script>
  import Modal from "./Modal.svelte";
  import AddPersonForm from "./AddPersonForm";
  let showModal = false;
  const toggleModal = () => {
    showModal = !showModal;
  };
  let people = [
    { name: "yoshi", beltColour: "black", age: 25, id: 1 }, // id is necessary with svelte to be used in the aech loop
    { name: "mario", beltColour: "orange", age: 45, id: 2 },
    { name: "luigi", beltColour: "brown", age: 35, id: 3 }
  ];
  const handleClick = id => {
    people = people.filter(person => person.id != id);
  };
  const addPerson = e => {
    const person = e.detail;
    people = [person, ...people];
    showModal = false;
  };
</script>
<Modal  showModal={showModal} on:click={toggleModal}>
  <AddPersonForm on:addPerson={addPerson}/>
</Modal> <!--shortcut only {showModal}-->
<!--prop called message is applied to the Modal--> 
<main>
<button class="main" on:click={toggleModal}>Open Modal</button>
{#each people as person(person.id)}  <!--here the id is applied-->
<div class="card">
    <div class="innercard">
      <h4>{person.name}</h4>
      {#if person.beltColour === "black"}
      <p><strong>MASTER NINJA</strong></p>
      {/if}
      <p>{person.age} years old , {person.beltColour} belt</p>
      <button on:click={() => handleClick(person.id)}>delete</button>
    </div>
</div>
{:else}
<p>There is no data ...</p>
{/each}
</main>
<style>
.card {
  border: 1px solid black;
  margin-left: 5px;
  width: 300px;
}
.innercard {
  padding: 10px;
  margin-bottom: 5px;
}
button.main{
  margin-left: 5px;
  margin-bottom:  10px;
  border-radius: 5px;
  padding: 5px;
  cursor: pointer;
}
button {
  border-radius: 5px;
  padding: 5px;
  cursor: pointer;
}
</style>