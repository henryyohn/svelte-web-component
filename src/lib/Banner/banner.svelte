<svelte:options tag="pi-custom-banner" />

<script>
  // component props
  // Camel case not supported for props, see drawback section.
  export let card_title, card_desc, card_img;
</script>

<slot>
  <a
    style="display: block;position: relative;max-width:1920px; margin: 0 auto;cursor: pointer;"
    href="https://pimax.com/pimax-frontier-2022/"
  >
    <picture class="Launch-item-picture">
      <source
        srcset="https://pimax.com/wp-content/uploads/2022/12/电脑端banner.png"
        media="(min-width:518px)"
      />
      <source
        srcset="https://pimax.com/wp-content/uploads/2022/12/手机端banner.png
"
        media="(max-width:517px)"
      />
      <img
        src="https://pimax.com/wp-content/uploads/2022/11/frontier-explore-1.png"
        alt="pimax frontier"
      />
    </picture>
    <img
      class="black5-maore"
      src="https://pimax.com/wp-content/uploads/2022/11/learnmore.png"
    />
  </a>
</slot>

<style>
  .black5-maore {
    width: clamp(100px, calc(0.1 * min(1920px, 100vw)), 120px);
    position: absolute;
    bottom: calc(0.1 * min(1920px, 100vw));
    left: calc(0.08 * min(1920px, 100vw));
  }
  img {
    max-width: 100%;
  }
  @media screen and (max-width: 518px) {
    .black5-maore {
      position: absolute;
      bottom: calc(0.63 * min(1920px, 100vw));
      left: 50%;
      transform: translateX(-50%);
    }
  }
</style>
