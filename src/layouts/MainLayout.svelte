<script lang="ts">
</script>

<style>
  .layout {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  .header, .footer {
    padding: 1rem;
    background-color: #f5f5f5;
    text-align: center;
  }

  .main {
    flex: 1;
    padding: 1rem;
  }
</style>

<div class="layout">
  <header class="header">
    <h1>Counter</h1>
  </header>

  <main class="main">
    <!-- ここにメインコンテンツが入ります -->
    <slot></slot>
  </main>

  <footer class="footer">
    © 2024 Steven
  </footer>
</div>
