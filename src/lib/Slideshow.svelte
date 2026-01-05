<script>
  export let slides = [];
  let current = 0;
  let imgEl;

  function prev() {
    current = (current - 1 + slides.length) % slides.length;
  }

  function next() {
    current = (current + 1) % slides.length;
  }

</script>

<div class="slideshow">
  <button class="prev" on:click={prev}>&#10094;</button>
  <img bind:this={imgEl} src={slides[current]} alt="Slide"/>
  <button class="next" on:click={next}>&#10095;</button>
  <div class="status">{current + 1} / {slides.length || 1}</div>
</div>

<style>
  .slideshow {
    position: relative;
    text-align: center;
  }

  .slideshow img {
    width: 100%;
    max-height: 300px;
    object-fit: cover;
    border-radius: 8px;
    cursor: pointer;
    display: block;
    transition: transform 0.2s;
  }

  .slideshow img:hover {
    transform: scale(1.01);
  }

  .prev,
  .next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    font-size: 1.6rem;
    background: rgba(0, 0, 0, 0.45);
    border: 1px solid rgba(255, 255, 255, 0.25);
    color: white;
    cursor: pointer;
    z-index: 1;
    width: 44px;
    height: 44px;
    border-radius: 50%;
    display: grid;
    place-items: center;
    transition: background 0.2s ease, transform 0.15s ease;
  }

  .prev:hover,
  .next:hover {
    background: rgba(0, 0, 0, 0.65);
    transform: translateY(-50%) scale(1.05);
  }

  .prev {
    left: 10px;
  }

  .next {
    right: 10px;
  }

  .status {
    position: absolute;
    right: 12px;
    bottom: 12px;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    padding: 6px 10px;
    border-radius: 999px;
    font-size: 0.9rem;
    border: 1px solid rgba(255, 255, 255, 0.25);
  }
</style>
