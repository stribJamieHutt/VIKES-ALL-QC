<script>
  import { createEventDispatcher, onMount } from 'svelte';
  const DATA_URL =
    'https://static.startribune.com/news/projects/all/2025-VIKES-ALLQC/data.json';
  let items = [];
  let loading = true;
  let error = '';
  export function addItem() {
    lines.push('blah');
    console.log(lines);
  }
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
    <div class="card card-{item.index}">
      <div class="poslabel">{item.position}</div>
      <div class="card-content">
        <div
          class="front"
          style="background-image:url('https://static.startribune.com{item.image_url}');background-position:bottom center;"
        ></div>
        <div class="back">
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
