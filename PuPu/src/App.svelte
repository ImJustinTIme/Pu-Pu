<script lang="ts">
  let files: FileList;
  let selectedFiles: FileList = new FileList();

  $: if (files) {
    // Note that `files` is of type `FileList`, not an Array:
    // https://developer.mozilla.org/en-US/docs/Web/API/FileList
    console.log(files);

    for (const file of files) {
      console.log(`${file.name}: ${file.size} bytes`);
    }
  }
</script>

<main class="container">
  <label for="many">Upload multiple files of any type:</label>
  <input bind:files id="many" multiple type="file" />

  <select multiple bind:value={selectedFiles}>
    {#if files}
      {#each files as file}
        <option value={file}>
          {file.name}
        </option>
      {/each}
    {/if}
  </select>
</main>

<style>
</style>

