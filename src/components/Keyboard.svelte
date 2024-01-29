<script>
  import { onMount, onDestroy } from "svelte";
  import VolumeSlider from "../shared/VolumeSlider.svelte";
  import CheckboxSlider from "../shared/CheckBoxSlider.svelte";
  import { fade } from "svelte/transition";

  const pianoKeys = [];
  let keys = [
    { key: "a", color: "white", bindIndex: 0 },
    { key: "w", color: "black", bindIndex: 1 },
    { key: "s", color: "white", bindIndex: 2 },
    { key: "e", color: "black", bindIndex: 3 },
    { key: "d", color: "white", bindIndex: 4 },
    { key: "f", color: "white", bindIndex: 5 },
    { key: "t", color: "black", bindIndex: 6 },
    { key: "g", color: "white", bindIndex: 7 },
    { key: "y", color: "black", bindIndex: 8 },
    { key: "h", color: "white", bindIndex: 9 },
    { key: "u", color: "black", bindIndex: 10 },
    { key: "j", color: "white", bindIndex: 11 },
    { key: "k", color: "white", bindIndex: 12 },
    { key: "o", color: "black", bindIndex: 13 },
    { key: "l", color: "white", bindIndex: 14 },
    { key: "p", color: "black", bindIndex: 15 },
    { key: "ç", color: "white", bindIndex: 16 },
  ];

  let volume = 0.5;
  let showKeys = true;

  const playTune = (key) => {
    const audio = new Audio(`/tunes/${key}.wav`); // create a new Audio object
    audio.volume = volume;
    audio.play();
    return audio; // return the Audio object
  };

  const handleKeyDown = (event) => {
    const key = event.key.toLowerCase();
    const keyObject = keys.find((k) => k.key === key);
    if (keyObject) {
      playTune(key);
      pianoKeys[keyObject.bindIndex].classList.add(`${keyObject.color}-active`);
      setTimeout(() => {
        pianoKeys[keyObject.bindIndex].classList.remove(
          `${keyObject.color}-active`
        );
      }, 200); // remove the class after 200ms
    }
  };

  onMount(() => {
    window.addEventListener("keydown", handleKeyDown);
  });

  onDestroy(() => {
    window.removeEventListener("keydown", handleKeyDown);
  });
</script>

<div class="wrapper">
  <header>
    <div class="top-elements">
      <h2>Virtual Piano</h2>
      <VolumeSlider bind:volume />
      <CheckboxSlider bind:checked={showKeys} />
    </div>
    <ul class="piano-keys">
      {#each keys as { key, color, bindIndex } (key)}
        <li
          class="key {color}"
          data-key={key}
          bind:this={pianoKeys[bindIndex]}
          on:click={() => playTune(key)}
          on:keydown={() => {}}
        >
          {#if showKeys}
            <span
              class="key-label"
              in:fade={{ duration: 500 }}
              out:fade={{ duration: 500 }}>{key}</span
            >
          {/if}
        </li>
      {/each}
    </ul>
  </header>
</div>

<style>
  .wrapper {
    width: 780px;
    border-radius: 20px;
    padding: 35px 40px;
    background: #141414;
  }
  .wrapper header {
    color: #b2b2b2;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .top-elements {
    display: flex;
    justify-content: space-between;
  }

  .key-label {
    transition: opacity 0.5s ease-in-out;
  }

  header h2 {
    font-size: 1.6rem;
  }

  .keys-checkbox {
    display: flex;
    align-items: center;
  }

  header .column span {
    font-weight: 500;
    margin-right: 15px;
    font-size: 1.19rem;
  }

  .piano-keys {
    display: flex;
    margin-top: 40px;
    margin-left: -10px;
  }
  .piano-keys .key {
    cursor: pointer;
    list-style: none;
    color: #a2a2a2;
    position: relative;
    user-select: none;
    text-transform: uppercase;
  }

  .piano-keys .white {
    width: 70px;
    height: 230px;
    border-radius: 8px;
    border: 1px solid #000;
    background: linear-gradient(#fff 96%, #eee 4%);
  }

  .piano-keys .white:active {
    box-shadow: inset -5px 5px 20px rgba(0, 0, 0, 0.2);
    background: linear-gradient(to bottom, #fff 0%, #eee 100%);
  }
  .piano-keys .black {
    width: 44px;
    height: 140px;
    margin: 0 -22px 0 -22px;
    z-index: 2;
    border-radius: 0 0 5px 5px;
    background: linear-gradient(#333, #000);
  }

  .piano-keys .black:active {
    box-shadow: inset -5px 5px 10px rgba(255, 255, 255, 0.1);
    background: linear-gradient(to bottom, #000, #434343);
  }

  .piano-keys span {
    position: absolute;
    bottom: 20px;
    width: 100%;
    font-size: 1.13rem;
    text-align: center;
  }

  .piano-keys .white-active {
    box-shadow: inset -5px 5px 20px rgba(0, 0, 0, 0.2);
    background: linear-gradient(to bottom, #fff 0%, #eee 100%);
  }

  .piano-keys .black-active {
    box-shadow: inset -5px 5px 10px rgba(255, 255, 255, 0.1);
    background: linear-gradient(to bottom, #000, #434343);
  }
</style>
