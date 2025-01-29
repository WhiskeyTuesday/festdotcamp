<script>
  import { X, Square, Minus } from "lucide-svelte";

  // always show time in New Orleans time
  let currentTime = new Date().toLocaleTimeString(
    "en-US",
    { timeZone: "America/Chicago" },
  );

  setInterval(() => {
    currentTime = new Date().toLocaleTimeString(
      "en-US",
      { timeZone: "America/Chicago" },
    );
  }, 1000);

  const handleMinimize = () => {
    alert("It's Windows ME Themed this time, I dunno why either");
  };

  const handleMaximize = () => {
    alert("go to www.mardi.camp for windows 98 theme Mardi Gras goodness");
  };

  const handleClose = () => {
    // haha gotem
    window.location.href = "https://www.youtube.com/watch?v=dQw4w9WgXcQ";
  };
</script>

<header class="winME-header">
  <div class="title-bar">
    <div class="title-bar-text">fest.camp - Tech Twitter New Orleans Jazz Fest 2025</div>
    <div class="title-bar-controls">
      <button aria-label="Minimize" on:click={handleMinimize}>
        <div><Minus size="16" color="#000" /></div>
      </button>
      <button aria-label="Maximize" on:click={handleMaximize}>
        <div><Square size="16" color="#000" /></div>
      </button>
      <button aria-label="Close" on:click={handleClose}>
        <div><X size="16" color="#000" /></div>
      </button>
    </div>
  </div>
  <nav class="winME-menu">
    <ul>
      <li>
        <a href="https://www.nojazzfest.com/music/">
          Official Festival Website
        </a>
      </li>
      <!-- <li><a href="#">j</a></li> -->
      <!-- <li><a href="#">Bar</a></li> -->
    </ul>
    <div class="system-tray">
      <span>{currentTime} in New Orleans</span>
    </div>
  </nav>
</header>

<style>
  .winME-header {
    background-color: #000080;
    color: #fff;
    padding: 2px;
  }

  .winME-menu {
    display: flex;
    background: var(--win-window);
    justify-content: space-between;
    padding: 0.25rem 0.5rem 0.25rem 0.5rem;
    border-bottom: 1px solid #888;
  }

 .winME-menu ul {
    padding: 0;
    margin: 0;
    display: flex;
    list-style-type: none;
  }

  .winME-menu a {
    color: #000;
    text-decoration: none;
  }

  .winME-menu a:hover {
    text-decoration: underline;
  }

  .title-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: linear-gradient(to right, var(--win-titlebar), #1084d0);
    /* css padding direction order is top right bottom left */
    padding: 0.25rem 0.5rem 0.25rem 0.5rem;
  }

  .title-bar-text {
    font-weight: bold;
  }

  .title-bar-controls button {
    width: 1.5rem;
    height: 1.33rem;
    background: var(--win-button);
    border: 1px solid #888;
    border-radius: 3px;
    box-shadow:
      inset -1px -1px #0a0a0a,
      inset 1px 1px #fff;
    }

    .title-bar-controls button div{
      display: flex;
      justify-content: center;
      align-items: center;
    }

  .system-tray {
    text-align: right;
    color: #000;
  }
</style>
