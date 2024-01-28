<div class="wrapper">
  <header>
    <div class="top-elements">
      <h2>Virtual Piano</h2>
      <div class="volume-slider">
        <span>Volume</span>
        <input type="range" min="0" max="100" value="50" />
      </div>
      <div class="keys-checkbox">
        <span>Show Keys</span>
        <input type="checkbox" checked />
      </div>
    </div>
    <ul class="piano-keys">
      <li class="key white"><span>a</span></li>
      <li class="key black"><span>w</span></li>
      <li class="key white"><span>s</span></li>
      <li class="key black"><span>e</span></li>
      <li class="key white"><span>d</span></li>
      <li class="key white"><span>f</span></li>
      <li class="key black"><span>t</span></li>
      <li class="key white"><span>g</span></li>
      <li class="key black"><span>y</span></li>
      <li class="key white"><span>h</span></li>
      <li class="key black"><span>u</span></li>
      <li class="key white"><span>j</span></li>
      <li class="key white"><span>k</span></li>
      <li class="key black"><span>o</span></li>
      <li class="key white"><span>l</span></li>
      <li class="key black"><span>p</span></li>
      <li class="key white"><span>ç</span></li>
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
  header h2 {
    font-size: 1.6rem;
  }

  .volume-slider,
  .keys-checkbox {
    display: flex;
    align-items: center;
  }

  header .column span {
    font-weight: 500;
    margin-right: 15px;
    font-size: 1.19rem;
  }

  .volume-slider input {
    outline: none;
    accent-color: #fff;
  }

  .volume-slider span,
  .keys-checkbox span {
    margin-right: 10px;
    margin-bottom: 8px;
  }

  .keys-checkbox input {
    width: 60px;
    height: 30px;
    appearance: none;
    position: relative;
    cursor: pointer;
    border-radius: 30px;
    background: #4b4b4b;
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
</style>
