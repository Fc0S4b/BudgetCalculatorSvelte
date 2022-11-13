<script>
  import { setContext } from 'svelte';
  // components
  import Navbar from './Navbar.svelte';
  import ExpensesList from './ExpensesList.svelte';
  import Totals from './Totals.svelte';
  import ExpenseForm from './ExpenseForm.svelte';
  // data
  import expensesData from './expenses';

  // variables
  let expenses = [...expensesData];
  // set editing variables
  let setName = '';
  let setAmount = null;
  let setId = null;
  // reactive
  $: total = expenses.reduce((acc, curr) => {
    return (acc += curr.amount);
  }, 0);
  // functions
  function removeExpense(id) {
    expenses = expenses.filter((item) => item.id !== id);
  }
  function clearExpenses() {
    expenses = [];
  }
  function addExpense({ name, amount }) {
    // console.log(name, amount);
    let expense = { id: Math.random() * Date.now(), name, amount };
    expenses = [expense, ...expenses];
  }
  function setModifiedExpense(id) {
    console.log('hello');
    let expense = expenses.find((item) => item.id === id);
    console.log(expense);
    setId = expense.id;
    setName = expense.name;
    setAmount = expense.amount;
    console.log({ setId, setName, setAmount });
  }
  // context
  setContext('remove', removeExpense);
  setContext('modify', setModifiedExpense);
</script>

<Navbar />
<main class="content">
  <ExpenseForm {addExpense} />
  <Totals title="total expenses" {total} />
  <ExpensesList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button
  >
</main>
