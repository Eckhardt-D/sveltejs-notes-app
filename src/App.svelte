<script>
  import Note from "./Note.svelte";
  let notes = [];
  let noteContent = "";

  // $: list = notes;

  const createNote = e => {
    e.preventDefault();

    if (noteContent !== "") {
      notes = [...notes, { content: noteContent }];
      noteContent = "";
    }
  };

  const deleteNote = evt => {
    const i = evt.detail;
    notes = notes.filter((note, index) => index !== i);
  };
</script>

<style>
  .container {
    margin: 0 30%;
  }

  .text-center {
    text-align: center;
  }

  .create-note {
    display: flex;
  }

  form {
    display: inherit;
    width: 100%;
  }

  .create-note input {
    flex-basis: 79%;
    margin-right: 1%;
  }

  .create-note button {
    flex-basis: 20%;
  }
</style>

<h1 class="text-center">Welcome to your notes app!</h1>
<div class="container">


  {#each notes as { content }, i}
    <Note on:deleteNote={deleteNote} index={i} note={content} />
  {/each}

  <div class="create-note">
    <form action="">
      <input bind:value={noteContent} type="text" required />
      <button type="submit" on:click={createNote}>Create</button>
    </form>
  </div>
</div>
