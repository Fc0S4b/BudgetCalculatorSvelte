<script>
  import { setContext } from 'svelte';
  // multiple context or one object with set of functions
  // const state = {
  //   name: 'simple name',
  //   remove: removeExpense,
  // };
  // components
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
  // context
  setContext('remove', removeExpense);
  // setContext('state', state);
</script>

<Navbar />
<main class="content">
  <ExpensesList {expenses} />
</main>
