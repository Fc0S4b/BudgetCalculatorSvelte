<script>
  import Navbar from './Navbar.svelte';
  import Title from './Title.svelte';
  let fruits = ['apple', 'orange', 'lemon'];
</script>

<Navbar />

{#each fruits as item}
  <!-- <h1>fruit: {item}</h1> -->
  <Title title={item} />
{/each}
