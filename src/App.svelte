<script>
  $: list = [];
  let textInput = '';
  let decision = '...';

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

  const makeChoice = () => {
    if (list.length) {
      const choice = list[Math.floor(Math.random() * list.length)];
      decision = 'The Decisionator says: ' + choice;
    }
  };

  const clearChoices = () => {
    list = [];
  };
</script>

<main class="flex justify-center items-center h-screen">
  <div>
    <h1 class="text-4xl font-bold text-center">The Decisionator</h1>
    <h3 class="text-2xl font-bold text-blue-600 text-center">{decision}</h3>
    <ol class="text-xl list-decimal my-2 ml-6">
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
    <div class="flex justify-center mt-2">
      <button
        class="bg-black font-bold text-white px-3 py-2 mx-1 rounded-md block"
        on:click={makeChoice}>Choose</button
      >
      <button
        class="bg-black font-bold text-white px-3 py-2 mx-1 rounded-md block"
        on:click={clearChoices}>Clear</button
      >
    </div>
  </div>
</main>
