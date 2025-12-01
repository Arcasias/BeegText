<script lang="ts">
  function onModeClick() {
    mode = mode === "light" ? "dark" : "light";
  }

  const prefersDark = window.matchMedia("(prefers-color-scheme: dark)").matches;
  let text: string = $state("Beeg Text");
  let mode = $state<"light" | "dark">(prefersDark ? "dark" : "light");
  let heading: HTMLHeadingElement;
</script>

<main
  class="{mode} bg-slate-200 text-slate-950 dark:bg-slate-950 dark:text-slate-200 overflow-auto"
>
  <h1
    class="flex justify-center items-center w-screen h-screen text-9xl font-bold m-0 text-center"
    bind:this={heading}
    bind:innerText={text}
    contenteditable="true"
  ></h1>
  <button class="fixed top-4 right-4 cursor-pointer" onclick={onModeClick}>
    {mode === "dark" ? "☀️" : "🌙"}
  </button>
</main>
