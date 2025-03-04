<script lang="ts">
  import PaperAirplanes from "./icons/PaperAirplanes.svelte";

  let { todos = $bindable([]) } = $props();

  let text = $state("");
  const maxHeight = 150;

  function autoResize(event: Event) {
    const textarea = event.target as HTMLTextAreaElement;

    textarea.style.height = "auto";

    const newHeight = Math.min(textarea.scrollHeight, maxHeight);
    textarea.style.height = `${newHeight}px`;
  }

  function handleSubmit(event: Event) {
    event.preventDefault();
    if (text.trim()) {
      todos = [...todos, { todo: text, isDone: false }];
      text = "";
    }
  }
</script>

<form
  onsubmit={handleSubmit}
  class="bg-white/40 border px-5 border-neutral-300 shadow-lg shadow-neutral-800/20 backdrop-blur-2xl w-full max-w-3xl rounded-lg p-3 mx-auto fixed left-1/2 -translate-x-1/2 bottom-10"
>
  <div class="flex items-end gap-x-5">
    <textarea
      bind:value={text}
      oninput={(event) => {
        autoResize(event);
      }}
      rows="1"
      class="w-full resize-none focus:outline-0 overflow-y-auto transition-all"
      placeholder="What needs to be done?"
    ></textarea>
    <button aria-label="Submit todo">
      <PaperAirplanes className="w-7 h-7 text-neutral-600" />
    </button>
  </div>
</form>

<style>
  /* your styles go here */
</style>
