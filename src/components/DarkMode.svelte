<script>
  let isDarkMode = false;

  function toggleDarkMode() {
    isDarkMode = !isDarkMode;
    
    // Сохраняем текущее состояние режима (например, в локальном хранилище)
    localStorage.setItem('isDarkMode', isDarkMode);
    
    // Применяем изменения к всему приложению
    applyDarkMode();
  }

  function applyDarkMode() {
    // Применяем стили к корневому элементу приложения или другим нужным элементам
    const app = document.querySelector('#app');
    if (isDarkMode) {
      app.classList.add('dark-mode');
    } else {
      app.classList.remove('dark-mode');
    }
  }

  // Проверяем сохраненное состояние режима при загрузке страницы
  if (localStorage.getItem('isDarkMode') === 'true') {
    isDarkMode = true;
    applyDarkMode();
  }
</script>

<style>
  /* Стили для свитчера */
  .switch-container {
    display: flex;
    align-items: center;
  }

  .switch-label {
    margin-right: 8px;
  }

  .switch {
    position: relative;
    display: inline-block;
    width: 60px;
    height: 34px;
  }

  .switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }

  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: .4s;
    transition: .4s;
    border-radius: 34px;
  }

  .slider:before {
    position: absolute;
    content: "";
    height: 26px;
    width: 26px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    -webkit-transition: .4s;
    transition: .4s;
    border-radius: 50%;
  }

  input:checked + .slider {
    background-color: #2196F3;
  }

  input:checked + .slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
  }

  /* Стили для dark mode */
  /* .dark-mode {
    background-color: #333;
    color: #fff;
  } */
</style>

<div class="switch-container">
  <span class="switch-label">Dark mode:</span>
  <label class="switch">
    <input type="checkbox" id="darkdome" name="darkmode" bind:checked={isDarkMode} on:change={toggleDarkMode}>
    <span class="slider"></span>
  </label>
</div>
