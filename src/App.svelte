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
  // context
  setContext('remove', removeExpense);

  function deleteExpense(event) {
    // console.log(event); // customEvent al presionar el botón delete, podemos obetener el id y name del objeto
    const {id, name} = event.detail;
    // console.log(name) //Hello from the expense
    removeExpense(id)
  }
</script>

<Navbar />
<main class="content">
  <ExpensesList {expenses} on:delete={deleteExpense} />
</main>
