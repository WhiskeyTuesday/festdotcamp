<script>
  import { onMount } from 'svelte';
  import mascot from '$lib/mascot.png';

  let marqueeText = "Welcome to jazzfest.camp - The ultimate (only) ingroup"
  + "twitter weirdo meetup at NO Jazz Fest 2025! (probably)";

  let stars = [];

 const MARDI_GRAS_COLORS = [
    '#582B7D', // Purple
    '#0AA14D', // Green
    '#B8860B'  // Gold
 ];

  const WINDOWS_ME_COLORS = [
    '#FFA500', // Orange
    '#008000', // Green
    '#FFFF00', // Yellow
    '#0000FF', // Blue
    '#FF0000',  // Red
  ];

  onMount(() => {
    const newStars = [];
    for (let i = 0; i < 50; i++) {
      newStars.push({
        x: Math.random() * 100,
        y: Math.random() * 100,
        baseSize: Math.random() * 3 + 5, // Random size for each star
        twinkleSpeed: 0.5 + Math.random(), // Random speed for each star
        offset: Math.random() * Math.PI * 2, // Random starting point in animation
        color: MARDI_GRAS_COLORS[Math.floor(Math.random() * 3)]
      });
    }
    stars = newStars;
  });
</script>

<div class="content-wrapper">
  <div class="win-ticker">
    <div class="ticker-content">{marqueeText}</div>
  </div>

  <div class="winME-window">
    <div class="window-title">fest.camp</div>
    <div class="window-content">
      <p>Come to jazzfest with your weird twitter friends!</p>
      <p>Dates: April 24th - 27th and May 1st-4th, 2025</p>
      <p class="text-sm text-gray-500">
        *I'll probably stay in NO the whole stretch but let me know
        which weekend you want to come to and I'll try to plan things
        if enough people are coming
      </p>
      <p>Location: New Orleans, Louisiana</p>
    </div>
  </div>

  <div class="winME-window">
    <div class="window-title">Vibes</div>
    <div class="window-content">
      <p>
        Jazz fest is a less chaotic vibe than Mardi Gras but
        then I'm old and lame and don't party that hard anyway
        so it's all the same to me. You won't have trouble
        finding trouble if you want to.
      </p>
      <p>
        The lineup this year looks pretty good at a glance.
        <a href="https://www.nojazzfest.com/lineup/">
          Check it out for yourself
        </a>
      </p>
    </div>
  </div>

  <div class="winME-window">
    <div class="window-title">Logistics</div>
    <div class="window-content">
      <p>
        Tickets are $320 per weekend if you buy them now
        (as of January 21st). The prices will go up and they
        will probably sell out but there are always one day
        tickets available on the street day of in my experience.
      </p>
      <p>
        There are also VIP tickets of various levels available
        if you're into that. They tend to sell out quickly so
        I'd get on it if you're interested.
        <a href="https://www.nojazzfest.com/tickets/">
          Click here to see all the options
        </a>
      </p>
      <p>
        I've got a reservation in the warehouse district for
        the full couple of weeks but I'm happy to help
        organize a big airbnb or whatever for either weekend
        or both. Let me know if you're interested and we'll
        start a group chat or something.
      </p>
    </div>
  </div>

  <div class="winME-window">
    <div class="window-title">Activities</div>
    <div class="window-content">
      The schedule doesn't usually get nailed down and released
      until way later but you can see the lineups so far at
      <a href="https://www.nojazzfest.com/music">The official
        website</a> and there are always a ton of other things
      to do in the city. Depending how many people come we
      can plan some group activities.
    </div>
  </div>

  <div class="winME-window">
    <div class="window-title">Featured Guests</div>
    <div class="window-content">
      <ul>
        <li>@WhiskeyTuesday</li>
      </ul>
    </div>
  </div>

  <div class="winME-window">
    <div class="window-title">Contact</div>
    <div class="window-content">
      <p>
        DM @WhiskeyTuesday on twitter if you're interested in coming
        or have any questions or want to help other people figure
        out their plans or want to organize something or want me
        to put you on the featured guest list or whatever.
      </p>
    </div>
  </div>

 <div class="space-background">
    {#each stars as star, i}
      <div
        class="star"
        style="
          left: {star.x}%;
          top: {star.y}%;
          --twinkle-speed: {star.twinkleSpeed}s;
          --size: {star.baseSize}px;
          --delay: {-star.offset}s;
          --star-color: {star.color};
        "
      >
      </div>
    {/each}
    <img src={mascot} alt="Mascot" class="mascot">
  </div>
</div>

<style>
  /* reinstate default HTML anchor styles */
  a {
    color: #00f;
    text-decoration: underline;
  }

  a:hover {
    text-decoration: none;
  }

  a:visited {
    color: #551a8b;
  }

  a:visited:hover {
    color: #551a8b;
  }

  .content-wrapper {
    padding: 10px;
    background-color: #008080;
    color: #fff;
  }

  .winME-window {
    background-color: #c0c0c0;
    border: 2px solid #fff;
    box-shadow: 2px 2px 0 #000;
    margin-bottom: 10px;
  }

  .window-title {
    background-color: #000080;
    color: #fff;
    padding: 0.25rem;
    padding-left: 0.5rem;
    font-weight: bold;
  }

  .window-content {
    padding: 10px;
    color: #000;
  }

  .space-background {
    position: relative;
    height: 200px;
    background-color: #fde1a2;
    overflow: hidden;
  }

  .star {
    position: absolute;
    border-radius: 50%;
    width: var(--size);
    height: var(--size);
    animation: twinkle var(--twinkle-speed) infinite ease-in-out;
    animation-delay: var(--delay);
  }

  @keyframes twinkle {
    0%, 100% {
      background-color: color-mix(in srgb, var(--star-color) 30%, transparent);
      transform: scale(0.8);
    }
    50% {
      background-color: var(--star-color);
      transform: scale(1.2);
    }
  }

  .mascot {
    position: absolute;
    bottom: 10px;
    right: 10px;
    max-width: 25%;
    animation: bounce 2s infinite;
  }

  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
  }

  .win-ticker {
    color: #000;
    background: var(--win-window);
    border: 2px solid var(--win-border);
    border-radius: 3px;
    box-shadow:
      inset -1px -1px #0a0a0a,
      inset 1px 1px #dfdfdf;
    padding: 3px;
    margin-bottom: 10px;
    overflow: hidden;
  }

  .ticker-content {
    animation: ticker 30s linear infinite;
    white-space: nowrap;
    display: inline-block;
  }

  @keyframes ticker {
    0% { transform: translateX(100%); }
    100% { transform: translateX(-100%); }
  }

  /* Add subtle hover effect to windows */
  .winME-window:hover {
    border-color: var(--win-titlebar);
  }

  .content-wrapper {
    padding: 10px;
    background: var(--win-background);
    color: var(--win-text);
    font-family: 'Microsoft Sans Serif', 'MS Sans Serif', sans-serif;
  }

  .winME-window {
    background: var(--win-window);
    border: 2px solid var(--win-border);
    border-radius: 3px;
    box-shadow:
      inset -1px -1px #0a0a0a,
      inset 1px 1px #dfdfdf,
      inset -2px -2px grey,
      inset 2px 2px #fff;
    margin-bottom: 10px;
  }

  .winME-window p {
    padding-bottom: 0.5rem;
  }

  .window-title {
    background: linear-gradient(to right, var(--win-titlebar), #1084d0);
    color: white;
    padding: 3px 5px 3px 5px;
    font-weight: bold;
  }

  /* Replace space background with Windows ME style */
  .space-background {
    background: linear-gradient(to bottom right, #3a6ea5, #1084d0);
    position: relative;
    height: 200px;
    overflow: hidden;
  }

  /* Update star styling to match Windows ME aesthetic */
  .star {
    background: rgba(255, 255, 255, 0.8) !important;
    box-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
  }

  /* Add Windows ME style scrollbar */
  ::-webkit-scrollbar {
    width: 16px;
  }

  ::-webkit-scrollbar-track {
    background: var(--win-button);
  }

  ::-webkit-scrollbar-thumb {
    background: var(--win-window);
    border: 1px solid #888;
    border-radius: 3px;
  }
</style>
