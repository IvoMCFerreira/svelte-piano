<script>
  export let checked = true;
</script>

<div class="keys-checkbox">
  <span>Show Keys</span>
  <div class="slider-wrapper">
    <input type="checkbox" bind:checked />
  </div>
</div>

<style>
  .keys-checkbox {
    display: flex;
    align-items: center;
  }
  .slider-wrapper {
    margin-left: 4px;
    margin-top: 4px;
  }
  .keys-checkbox input {
    width: 60px;
    height: 30px;
    appearance: none;
    position: relative;
    cursor: pointer;
    border-radius: 30px;
    background: #4b4b4b;
    transition: background 0.3s;
  }

  .keys-checkbox input::before {
    content: "";
    height: 20px;
    width: 20px;
    top: 50%;
    left: 5px;
    border-radius: inherit;
    position: absolute;
    background: #8c8c8c;
    transform: translateY(-50%);
    transition: all 0.3s ease;
  }

  .keys-checkbox input:checked {
    background: #4b4b4b;
  }

  .keys-checkbox input:checked::before {
    left: calc(100% - 5px);
    transform: translate(-100%, -50%);
    background: #ffffff;
  }

  .keys-checkbox span {
    margin-right: 10px;
    margin-bottom: 8px;
  }
</style>
