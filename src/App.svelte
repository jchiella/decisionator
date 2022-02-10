<script>
  import { listen, text } from 'svelte/internal';

  $: list = [];
  let textInput = '';

  const addItem = () => {
    if (textInput !== '') {
      list = [...list, textInput];
      textInput = '';
    }
  };

  const handleKeypress = (e) => {
    if (e.key === 'Enter') {
      addItem();
    }
  };
</script>

<main class="flex justify-center items-center h-screen">
  <div>
    <h1 class="text-4xl font-bold">The Decisionator</h1>
    <ol class="text-xl list-decimal my-2">
      {#each list as item}
        <li>{item}</li>
      {/each}
    </ol>
    <div class="flex">
      <input
        on:keypress={handleKeypress}
        bind:value={textInput}
        type="text"
        class="border-2 border-black rounded-xl flex-grow mr-1 py-1 px-1 text-xl"
      />
      <button
        class="bg-black font-bold text-white px-3 rounded-xl"
        on:click={addItem}>+</button
      >
    </div>
  </div>
</main>
