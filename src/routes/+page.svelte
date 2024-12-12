<script lang="ts">
  import Hill0 from '$lib/hills/Hill0.svelte';
  import Hill1 from '$lib/hills/Hill1.svelte';
  import Hill2 from '$lib/hills/Hill2.svelte';
  import Hill3 from '$lib/hills/Hill3.svelte';
  import Arrow from '$lib/Arrow.svelte';
  import Check from '$lib/Check.svelte';
  import RotatingSphere from './RotatingSphere.svelte';
  import Sparkles from '$lib/Sparkles.svelte';
  import Sphere from '$lib/Sphere.svelte';
  import OnePasswordLight from '$lib/logos/1PasswordLight.svg';
  import DisneyLight from '$lib/logos/DisneyLight.svg';
  // import RedBull from '$lib/logos/RedBull.svg';
  import CodeForCause from '$lib/logos/CodeForCause.svg';
  import Desmos from '$lib/logos/Desmos.svg';
  import Axure from '$lib/logos/Axure.svg';
  import CodeCrafters from '$lib/logos/CodeCrafters.png';
  import InterviewBuddy from '$lib/logos/InterviewBuddy.png';
  import Mos from '$lib/logos/mos_logo_3.png';
  import { enhance } from '$app/forms';

  let button: HTMLButtonElement | undefined = $state();
</script>

<svelte:head>
  <title>Zenith Hacks</title>
  <meta name="description" content="Zenith is a hackathon in the SFO for teens coming next year." />
  <!-- TODO: Add structured data: https://developers.google.com/search/docs/appearance/structured-data/event#structured-data-type-definitions -->
</svelte:head>

<div class="scenery">
  <!-- Header -->
  <Sparkles />
  <div class="zenith-header">
    <h1>
      <span class="no-break">
        {#each Array.from('Zenith').entries() as [idx, char]}
          <span style="--idx: {idx}" class="header-element">{char}</span>
        {/each}
      </span>
      <span class="no-break">
        {#each Array.from('2025').entries() as [idx, char]}
          <span style="--idx: {idx + 7}" class="header-element date">{char}</span>
        {/each}
      </span>
    </h1>
    <p class="header-promo">
      Zenith is a hackathon in the SFO for teens led by the Hack Club community coming next year. Join us and make
      something awesome!
    </p>
    <form
      class="outer-email-form"
      method="POST"
      action="/?/email"
      use:enhance={() => {
        button?.classList.add('loading');
        button?.setAttribute('disabled', '');
        return async ({ update }) => {
          await update();

          button?.classList.remove('loading');
          button?.classList.add('loaded');
        };
      }}
    >
      <p>We'll send you a maximum of two emails a week! Unsubscribe anytime.</p>
      <label for="email">Your email</label>
      <div class="email-form">
        <input
          id="email"
          type="email"
          name="email"
          placeholder="sarah@example.com"
          required
          data-lp-igore
          data-lpignore="true"
          data-bwignore
          data-form-type="other"
        />
        <button id="submit" type="submit" class="" aria-label="Submit" bind:this={button}>
          <div class="arrow">
            <Arrow />
          </div>
          <div class="check">
            <Check />
          </div>
        </button>
      </div>
      <p class="legal">
        We collect your IP address and approximate location. By submitting, you agree that you've read our <a
          href="/privacy">privacy policy</a
        >.
      </p>
    </form>
  </div>

  <!-- Scenery and big circle -->
  <div class="scenery-hills" aria-hidden="true">
    <div class="scenery-hill-wrapper" style="z-index: 1; --fill: var(--bg-30)">
      <Hill0></Hill0>
    </div>
    <div class="scenery-hill-wrapper" style="z-index: 2; --fill: var(--bg-20); --last-fill: var(--bg-30)">
      <Hill1></Hill1>
    </div>
    <div class="scenery-hill-wrapper" style="z-index: 3; --fill: var(--bg-10); --last-fill: var(--bg-20)">
      <Hill2></Hill2>
    </div>

    <RotatingSphere style="z-index: 3" />

    <div class="scenery-hill-wrapper" style="z-index: 5; --fill: var(--bg); --last-fill: var(--bg-10)">
      <Hill3></Hill3>
    </div>
  </div>
</div>

<article class="info">
  <h2>What is Zenith?</h2>
  <div>
    <div>
      <p>
        Zenith 2025 is a hackathon in San Francisco organised by and for teens. Join us for 2 days to share and
        collaborate with like minded individuals in a supportive, mistake friendly environment.
      </p>
    </div>
    <enhanced:img loading="lazy" src="$lib/images/eclipse.webp" alt="Eclipse" />
  </div>
</article>

<article class="info info-right">
  <h2>What's a hackathon?</h2>
  <div>
    <div>
      <p>
        <!-- TODO: Change this -->
        A hackathon is a social event focused on coding where teenagers come together to learn, build, and share their results
        with others!
      </p>
    </div>
    <enhanced:img
      loading="lazy"
      src="$lib/images/hackathon.jpg"
      alt="A hackathon. There are tables arranged in rows and people with laptops sitting at them."
    />
  </div>
</article>

<article class="info">
  <h2>Can I come?</h2>
  <div>
    <div>
      <p>You'll need to bring a laptop and an enthusiasm for technology!</p>
      <br />
      <p>
        However, we understand that not everyone can afford to come to Zenith. Thanks to our sponsors, we're able to pay
        for your travels if you can't pay for your travels&mdash;even if you live outside of the US. We've got limited
        funds, so apply early if you need help with paying for travel.
      </p>
    </div>
    <div class="image-box">
      <Sphere />
    </div>
  </div>
</article>

<article>
  <div class="info">
    <h2>Our sponsors</h2>
    <p>This event wouldn't have been possible without the help of:</p>
  </div>

  <div class="sponsors">
    <img loading="lazy" src={OnePasswordLight} alt="1Password logo" />
    <img loading="lazy" src={DisneyLight} alt="Disney logo" />
    <img loading="lazy" src={CodeForCause} alt="Code for Cause logo" />
    <img loading="lazy" src={Desmos} alt="Desmos logo" />
    <img loading="lazy" src={Axure} alt="Axure logo" />
    <img loading="lazy" src={CodeCrafters} alt="CodeCrafters logo" />
    <img loading="lazy" src={InterviewBuddy} alt="InterviewBuddy logo" />
    <img loading="lazy" src={Mos} alt="MOS logo" />
    <!-- <img loading="lazy" src={RedBull} alt="RedBull logo" /> -->
  </div>

  <div class="info">
    <p>As well as these individual donors:</p>
  </div>

  <div class="sponsors">
    <p>John Tan-Aristy</p>
    <p>Sarah</p>
    <p>HackSchools Foundation</p>
    <p>Jakub Wojtak</p>
    <p>Arnav Kumar</p>
    <p>Briyan Dyju</p>
  </div>

  <div class="info">
    <p>
      If you'd like to help out, you can
      <a href="https://hcb.hackclub.com/donations/start/zenithhacks">donate to us as an individual</a>
      or get in touch at
      <a href="mailto:team@zenithhacks.org">team@zenithhacks.org</a>. Thank you!
    </p>
  </div>
</article>

<style>
  /* Scenery styles */

  .scenery {
    /* Viewport box that contains the hills and the circle Thing */
    background: rgb(var(--bg-n10));

    width: 100%;
    height: 100vh;

    display: flex;
    flex-direction: column;
  }

  .scenery > :global(svg) {
    /* Sparkles */
    display: none;
    z-index: 0;
    position: absolute;
    top: 0;
    left: calc(max(1024px, 100vw - 100%));
  }

  /* Header styles */

  @keyframes header {
    0% {
      font-variation-settings: 'wght' 300;
      transform: translateY(-200%);
    }

    50% {
      font-variation-settings: 'wght' 400;
      transform: translateY(0);
    }

    100% {
      font-variation-settings: 'wght' 700;
      transform: translateY(0);
    }
  }

  h1 {
    font-family: 'Zenith Title Grotesk', 'Zenith Grotesk', monospace, system-ui, sans-serif;
    font-size: 4em;
    line-height: 1;
    width: min-content;
  }

  h1 .header-element {
    display: inline-block;
    transform: translateY(-200%);
    font-variation-settings: 'wght' 400;
    animation: header 1s calc(var(--idx) * 0.05s) forwards;
  }

  @media (prefers-reduced-motion) {
    h1 .header-element {
      font-variation-settings: 'wght' 700;
      animation: none;
    }
  }

  h1 .no-break {
    display: inline-block;
    min-width: max-content;
    overflow: clip;
  }

  .header-promo {
    font-size: 1.2em;
    line-height: 1.2;
  }

  .date {
    color: rgb(var(--green));
  }

  .zenith-header {
    z-index: 2;
    display: flex;
    flex-direction: column;
    gap: 0.5em;
    padding: 2em;
  }

  .legal {
    opacity: 90%;
    font-size: 0.8em;
    max-width: 100%;
  }

  @media (min-width: 640px) and (min-height: 640px) {
    h1 {
      font-size: 6em;
      width: max-content;
    }

    .header-promo {
      font-size: 2em;
    }

    .zenith-header {
      width: min-content;
    }
  }

  @media (min-width: 1024px) and (min-height: 640px) {
    h1 {
      font-size: 8em;
    }

    .zenith-header {
      padding: 4em;
    }

    .scenery > :global(svg) {
      display: block;
    }
  }

  /* Form styles */

  .outer-email-form {
    display: flex;
    flex-direction: column;
    gap: 0.5em;
    margin-top: 1em;
  }

  .outer-email-form > label {
    font-size: 0.8em;
  }

  .email-form {
    display: flex;
    flex-direction: row;
    gap: 1em;
    max-width: 32em;
  }

  .email-form > * {
    height: 3em;
  }

  .email-form > input {
    flex: 1 1 0;
    min-width: 0;
    padding-left: 1.5em;
  }

  .email-form > button {
    flex: 0 0 3em;
    padding: 0;
  }

  .email-form > button > * {
    margin: auto;
    width: min-content;
  }

  .email-form > button > .arrow {
    fill: rgb(var(--bg));
    transition:
      transform 200ms,
      background 200ms;
    transform: translateX(0);
  }

  .email-form > button:hover > .arrow {
    transform: translateX(0.2em);
  }

  .email-form > button > .check {
    display: none;
  }

  .email-form > button :global(svg) {
    fill: rgb(var(--bg));
  }

  .email-form > button:global(.loading) {
    background: rgba(var(--fg), 80%);
  }

  .email-form > button:global(.loaded) {
    background: rgb(var(--green));
  }

  .email-form > :global(button.loaded > .check) {
    display: block;
  }

  .email-form > :global(button.loaded > .arrow) {
    display: none;
  }

  /* Scenery */

  .scenery-hills {
    position: relative;
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
    width: 100%;
    min-height: 0;
    flex: 1 1 auto;
    overflow: clip;
    gap: 0;

    container-name: scenery;
    container-type: size;
  }

  .scenery-hill-wrapper {
    flex: auto;
    display: flex;
    max-height: 240px;
    min-height: 0;
    justify-content: center;
  }

  .scenery-hill-wrapper :global(svg) {
    min-width: 1920px;
    width: 100vw;
    overflow: visible;
  }

  .scenery-hill-wrapper :global(path) {
    fill: rgb(var(--fill));
    filter: drop-shadow(0px -4px 4px rgba(83, 83, 83, 0.25));
  }

  @container scenery (min-height: 490px) {
    .scenery-hill-wrapper {
      background: rgb(var(--last-fill));
    }
  }

  /* Info bars */

  .info {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    padding: 2rem;
    margin: auto;
    max-width: 1024px;
    font-size: 1.2em;
  }

  .info > div {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .info > div > div {
    min-width: 0;
    flex: 1 1 0;
  }

  .image-box,
  .info picture {
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgb(var(--fg));
    box-shadow: 0.5em 0.5em rgb(var(--bg-30));
    min-height: 200px;
  }

  .image-box :global(path) {
    stroke: rgb(var(--bg));
  }

  @media (min-width: 640px) {
    .info > div {
      flex-direction: row;
    }

    .image-box,
    .info picture {
      max-width: 50%;
      aspect-ratio: 2;
      object-fit: cover;
    }

    .image-box,
    .info img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .info-right {
      text-align: right;
    }

    .info-right > div {
      flex-direction: row-reverse;
    }

    .info-right .image-box {
      box-shadow: -0.5em 0.5em rgb(var(--bg-30));
    }
  }

  @media (min-width: 1024px) {
    .info {
      padding: 4rem;
    }
  }

  /* Sponsors */

  .sponsors {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    padding: 0 2em;
    gap: 1em;
    width: 100%;
  }

  .sponsors > * {
    flex: 1 1 auto;
    background: rgb(var(--bg-20));
    box-shadow: 0.5rem 0.5rem rgb(var(--bg-30));
    padding: 1rem;
  }

  .sponsors > img {
    height: 6em;
    object-fit: contain;
  }

  article:not(.info) {
    margin-bottom: 4em;
  }

  .sponsors > p {
    text-align: center;
    font-family: 'Zenith Grotesk', monospace, system-ui, sans-serif;
    font-weight: bolder;
    font-size: 1.3em;
  }

  @media (min-width: 1024px) {
    .sponsors {
      padding: 0 4em;
    }
  }
</style>
