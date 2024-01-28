<script>
  import { onMount } from "svelte";
  import * as Tone from "tone";

  // Define the notes for two octaves (24 notes)
  const notes = [
    "C3",
    "C#3",
    "D3",
    "D#3",
    "E3",
    "F3",
    "F#3",
    "G3",
    "G#3",
    "A3",
    "A#3",
    "B3",
    "C4",
    "C#4",
    "D4",
    "D#4",
    "E4",
    "F4",
    "F#4",
    "G4",
    "G#4",
    "A4",
    "A#4",
    "B4",
  ];

  // Initialize Tone.js synth
  const synth = new Tone.Synth().toDestination();

  // Play a note when a key is pressed
  function playNote(note) {
    synth.triggerAttackRelease(note, "8n");
  }

  // Handle key press events
  function handleKeyPress(event) {
    // Map key press to corresponding note index
    const keyIndex = event.keyCode - 65; // Map A to index 0, B to index 1, and so on

    // Check if the key corresponds to a valid note
    if (keyIndex >= 0 && keyIndex < notes.length) {
      playNote(notes[keyIndex]); // Play the corresponding note
    }
  }

  // Add event listener when the component is mounted
  onMount(() => {
    window.addEventListener("keydown", handleKeyPress);

    // Remove event listener when the component is unmounted
    return () => {
      window.removeEventListener("keydown", handleKeyPress);
    };
  });
</script>

<!-- Render the keyboard UI -->
<div>
  {#each notes as note}
    <button on:click={() => playNote(note)}>{note}</button>
  {/each}
</div>

<style>
  /* Add styling for the keyboard keys */
  /* You can customize the styling as needed */
</style>
