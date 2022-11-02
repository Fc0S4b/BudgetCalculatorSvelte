<script>
  import Navbar from './Navbar.svelte';
  import Title from './Title.svelte';
  import Example from './Example.svelte';
</script>

<!-- <style></style> -->
<!-- CSS/STYLING -->

<Navbar />
<Title title="add expense" />
<Title title="expense list" />
<Title />
<Example />
<span>hello from app</span>

<style>
  /* no name collisions */
  /* css bundle gestiona las clases añadiendo id únicos */
  span {
    background: green;
    color: blue;
  }
</style>
