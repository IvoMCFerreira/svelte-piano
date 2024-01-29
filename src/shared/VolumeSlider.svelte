<script>
  export let volume = 0.5;
</script>

<div class="volume-slider">
  <span>Volume</span>
  <input type="range" min="0" max="1" step="0.01" bind:value={volume} />
</div>

<style>
  .volume-slider {
    display: flex;
    align-items: center;
  }

  .volume-slider input {
    outline: none;
    accent-color: #fff;
  }

  .volume-slider span {
    margin-right: 10px;
    margin-bottom: 8px;
  }
</style>
