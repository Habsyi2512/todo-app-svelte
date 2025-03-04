<script lang="ts">
  import FormInput from "./components/FormInput.svelte";

  let todos: { todo: string; isDone: boolean }[] = $state([]);
</script>

<main class="bg-[url('/background.jpg')] min-h-screen pt-[30px]">
  <div
    class="bg-white/40 border border-neutral-300 shadow-lg shadow-neutral-800/20 backdrop-blur-2xl w-full max-w-3xl rounded-lg mx-auto"
  >
    <h1 class="text-3xl font-bold text-center py-5 text-neutral-600">
      Todo APP
    </h1>

    {#each todos as todo}
      <li>{todo.todo}</li>
    {:else}
      <div>Tidak Ada todo</div>
    {/each}
  </div>

  <FormInput {todos} />
</main>

<style></style>
