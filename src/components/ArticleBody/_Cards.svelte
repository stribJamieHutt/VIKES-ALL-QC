<script>
  import { createEventDispatcher, onMount } from 'svelte';
  const DATA_URL =
    'https://static.startribune.com/news/projects/all/2025-VIKES-ALLQC/data.json';
  let items = [];
  let loading = true;
  let error = '';

  onMount(async () => {
    try {
      const res = await fetch(DATA_URL);
      if (!res.ok) throw new Error(`HTTP ${res.status}`);
      const json = await res.json();
      if (!Array.isArray(json))
        throw new Error('Unexpected data format (expected array).');
      items = json;
      // console.log('FIRST ROW SAMPLE:', items[0], Object.keys(items[0] || {}));
    } catch (e) {
      error = e?.message || String(e);
    } finally {
      loading = false;
    }
  });
</script>

<div class="card-list">
  {#each items as item}
    <div class="card card-{items.indexOf(item) + 1}">
      <div class="poslabel">{item.position}</div>
      <div class="card-content">
        <div
          class="card-front"
          style="background-image:url('https://static.startribune.com{item.image_url}');background-position:bottom center;"
        ></div>
        <div class="card-back">
          <div class="cardback-content">
            <div class="card-header">
              <div class="nameplate">{item.name}</div>
              <div class="posinfo">
                <span class="name">{item.position}</span>
                <span class="jersey_num">{item.jersey_number}</span>
                <span class="years">{item.years}</span>
              </div>
            </div>
            <div class="blurb">
              <span class="blurb-text">{item.blurb}</span>
              <span class="attrib">&mdash; {item.blurb_author}</span>
              <span class="other_voters"
                >Also recieving votes:<br />{item.other_votes}</span
              >
            </div>
            <div class="fadedScroller_fade"></div>
          </div>
        </div>
      </div>
    </div>
  {/each}
</div>

<style>
  /* The flip card container - set the width and height to whatever you want. We
have added the border property to demonstrate that the flip itself goes out of
the box on hover (remove perspective if you don't want the 3D effect */
  .flip-card {
    background-color: transparent;
    width: 300px;
    height: 200px;
    border: 1px solid #f1f1f1;
    perspective: 1000px; /* Remove this if you don't want the 3D effect */
  }

  /* This container is needed to position the front and back side */
  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }

  /* Do an horizontal flip when you move the mouse over the flip box container */
  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  /* Position the front and back side */
  .flip-card-front,
  .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;
  }

  /* Style the front side (fallback if image is missing) */
  .flip-card-front {
    background-color: #bbb;
    color: black;
  }

  /* Style the back side */
  .flip-card-back {
    background-color: dodgerblue;
    color: white;
    transform: rotateY(180deg);
  }
</style>
