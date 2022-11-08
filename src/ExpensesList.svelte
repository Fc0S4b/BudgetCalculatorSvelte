<script>
  import SectionTitle from './Title.svelte';
  import Expense from './Expense.svelte';
  export let expenses = [];
  export let removeExpense;
</script>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense, index}
      <!-- <Expense index={index + 1} /> -->
      <Expense {...expense} {removeExpense} />
    {:else}
      <h2>currently you have no expenses</h2>
    {/each}
  </ul>
</section>

<style>
  h2 {
    text-transform: capitalize;
  }
</style>
