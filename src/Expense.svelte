<script>
  // export let index;
  // export let expense;
  // let { name, amount, id } = expense;
  // si pasas el prop con spread operator, puedes recuperar las props así: (los iguales son valores default)
  export let id;
  export let name = '';
  export let amount = 0;
  let displayAmount = false;
  function toggleAmount() {
    displayAmount = !displayAmount;
  }
</script>

<article class="single-expense">
  <div class="expense-info">
    <!-- on:click|once once es modifiers que hace que se ejecute solo una vez la función de onclick, hay varios mas como preventDefault -->
    <h2>
      {name}
      <button class="amount-btn" on:click={toggleAmount}>
        <i class="fas fa-caret-down" />
      </button>
    </h2>
    {#if displayAmount}
      <h4>amount : ${amount}</h4>
    {/if}
  </div>
  <div class="expense-buttons">
    <button class="expense-btn edit-btn">
      <i class="fas fa-pen" />
    </button>
    <button class="expense-btn delete-btn">
      <i class="fas fa-trash" />
    </button>
  </div>
</article>
