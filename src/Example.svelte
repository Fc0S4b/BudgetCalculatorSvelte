<span>
  hello from example

  <div class="main-title">
    <h2>example title</h2>
  </div>
</span>

<style>
  /* fijar span a estilos globales, debes comentar los estilos del otro span */
  :global(span) {
    background: var(--primaryColor);
    color: white;
  }
  .main-title {
    color: red;
  }
</style>
