<script>
  // export let index;
  // export let expense;
  // let { name, amount, id } = expense;
  // si pasas el prop con spread operator, puedes recuperar las props así: (los iguales son valores default)
  export let id;
  export let name = '';
  export let amount = 0;
</script>

<div>
  <!-- <p>{index}</p> -->
  <!-- puede ser expense.name o expense.amount, pero mejor destructurado -->
  <h1>title : {name}</h1>
  <h1>amount : {amount}</h1>
</div>
