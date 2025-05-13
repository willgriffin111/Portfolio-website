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

  function viewFullscreen() {
    if (imgEl && imgEl.requestFullscreen) {
      imgEl.requestFullscreen();
    } else if (imgEl && imgEl.webkitRequestFullscreen) {
      imgEl.webkitRequestFullscreen(); // Safari
    } else if (imgEl && imgEl.msRequestFullscreen) {
      imgEl.msRequestFullscreen(); // IE11
    }
  }
</script>

<div class="slideshow">
  <button class="prev" on:click={prev}>&#10094;</button>
  <img bind:this={imgEl} src={slides[current]} alt="Slide" on:click={viewFullscreen} />
  <button class="next" on:click={next}>&#10095;</button>
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
    font-size: 2rem;
    background: none;
    border: none;
    color: white;
    cursor: pointer;
    z-index: 1;
  }

  .prev {
    left: 10px;
  }

  .next {
    right: 10px;
  }
</style>
