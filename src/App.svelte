<script>
  import { setContext } from 'svelte';

  import Navbar from './Navbar.svelte';
  import ExpensesList from './ExpensesList.svelte';
  // data
  import expensesData from './expenses';
  import Expense from './Expense.svelte';
  // variables
  let expenses = [...expensesData];
  // functions
  function removeExpense(id) {
    expenses = expenses.filter((item) => item.id !== id);
  }
  function clearExpenses() {
    expenses = [];
  }
  // context
  setContext('remove', removeExpense);
</script>

<Navbar />
<main class="content">
  <ExpensesList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button
  >
</main>
