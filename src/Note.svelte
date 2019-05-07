<script>
  export let note;
  export let index;

  import { createEventDispatcher } from "svelte";
  import { fade, fly } from "svelte/transition";

  const dispatch = createEventDispatcher();

  function deleteNote() {
    dispatch("deleteNote", index);
  }
</script>

<style>
  .card {
    padding: 15px;
    border: 1px solid black;
    margin: 15px auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .card span {
    border: 0.5px solid grey;
    font-family: monospace;
    padding: 0px 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: red;
    color: white;
    cursor: pointer;
  }
</style>

<div in:fade out:fly={{ x: 500, duration: 500 }} class="card">
  <p contenteditable="true"> {note}</p>
  <span on:click={deleteNote}>x</span>
</div>
