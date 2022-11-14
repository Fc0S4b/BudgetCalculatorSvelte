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
  $: isEditing = setId ? true : false;
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
  function handleSubmit() {
    if (isEditing) {
      editingExpense();
    } else {
      addExpense();
    }
    setId = null;
    setAmount = null;
    setName = '';
  }
  $: console.log({ setName, setAmount });
  // function addExpense({ name, amount }) {
  //   // console.log(name, amount);
  //   let expense = { id: Math.random() * Date.now(), name, amount };
  //   expenses = [expense, ...expenses];
  // }
  function addExpense() {
    // console.log(name, amount);
    let expense = { id: Math.random(), name: setName, amount: setAmount };
    expenses = [expense, ...expenses];
  }
  function setModifiedExpense(id) {
    let expense = expenses.find((item) => item.id === id);

    setId = expense.id;
    setName = expense.name;
    setAmount = expense.amount;
  }
  // function editingExpense({ name, amount }) {
  //   expenses = expenses.map((item) => {
  //     return item.id === setId ? { ...item, name, amount } : { ...item };
  //   });
  //   setId = null;
  //   setAmount = null;
  //   setName = '';
  // }
  function editingExpense() {
    expenses = expenses.map((item) => {
      return item.id === setId
        ? { ...item, name: setName, amount: setAmount }
        : { ...item };
    });
    // setId = null;
    // setAmount = null;
    // setName = '';
  }
  // context
  setContext('remove', removeExpense);
  setContext('modify', setModifiedExpense);
</script>

<Navbar />
<main class="content">
  <ExpenseForm
    bind:name={setName}
    bind:amount={setAmount}
    {handleSubmit}
    {isEditing}
  />
  <Totals title="total expenses" {total} />
  <ExpensesList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button
  >
</main>
