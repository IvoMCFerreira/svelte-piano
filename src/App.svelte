<script>
  import Keyboard from "./components/Keyboard.svelte"; // Import the Keyboard component
</script>

<main>
  <head
    ><link
      rel="stylesheet"
      href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap"
    />
  </head>
  <Keyboard />
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Poppins", sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background: #e3f2fd;
  }
</style>
