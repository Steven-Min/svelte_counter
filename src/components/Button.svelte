<script lang="ts">
  export let text: string = 'Button'; // ボタンのテキスト
  export let onClick: () => void; // クリックイベントのハンドラ
  export let className: string = ''; // 追加のCSSクラス
</script>

<style>
  .button {
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
    outline: none;
    margin-bottom: 0;
  }

  .button:hover {
    background-color: #0056b3;
  }

  .button:active {
    background-color: #004094;
  }
</style>

<button class="button {className}" on:click={onClick}>
  {text}
</button>
