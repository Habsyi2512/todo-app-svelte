<script lang="ts">
  import FormInput from "./components/FormInput.svelte";
  import { fade } from "svelte/transition";
  import type { TodosProps } from "./interface/interface";

  let todos: TodosProps[] = $state([]);
</script>

<main class="bg-[url('/background.jpg')] min-h-screen pt-[30px]">
  <div
    class="bg-white/40 border border-neutral-300 shadow-lg shadow-neutral-800/20 backdrop-blur-2xl w-full max-w-3xl rounded-lg mx-auto"
  >
    <h1 class="text-3xl font-bold text-center py-5 text-neutral-600">
      Todo APP
    </h1>

    <div class="p-4">
      {#each todos as todo}
        <li class="border" transition:fade>{todo.todo}</li>
      {:else}
        <p class="text-center font-bold text-neutral-600">Tidak Ada todo</p>
      {/each}
    </div>
  </div>

  <FormInput bind:todos />
</main>

<style></style>
