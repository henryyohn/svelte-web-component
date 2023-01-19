<!--Add this line to your web component-->
<svelte:options tag="my-counter" />

<script>
  let count = 0;
  let timer = null;
  let status = "";
  const countdown = () => {
    timer = setTimeout(() => {
      count = count + 1;
      countdown();
    }, 1000);
  };
  const stop = () => {
    if (timer) {
      timer && clearTimeout(timer);
      timer = null;
      status = "stop";
    } else {
      countdown();
      status = "running";
    }
  };
</script>

<p>{status}</p>
<button on:click={stop}>
  count seconds: {count}
</button>

<style>
  button {
    border: 1px solid #000;
    background-color: #fff;
    padding: 1.5em;
    border-radius: 10px;
    cursor: pointer;
  }
</style>
