<script>
  import { theme } from '../store.js'

  function toggle() {
    const newTheme = $theme === 'dark' ? 'light' : 'dark'
    theme.set(newTheme)
    localStorage.setItem('theme', newTheme)
  }

  $: checked = $theme === 'dark'
</script>

<div class="flex justify-center">
  <div class="flex items-center space-x-4">
    <svg
      class="text-lime-500 dark:text-gray-700"
      width="32"
      height="32"
      fill="currentColor"
      ><path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M16 2a1.4 1.4 0 011.4 1.4v1.4a1.4 1.4 0 11-2.8 0V3.4A1.4 1.4 0 0116 2zM6.1 6.1a1.4 1.4 0 011.98 0l.99.99a1.4 1.4 0 11-1.98 1.98l-.99-.99a1.4 1.4 0 010-1.98zm19.8 0a1.4 1.4 0 010 1.98l-.99.99a1.4 1.4 0 01-1.98-1.98l.99-.99a1.4 1.4 0 011.98 0zM9 16a7 7 0 1114 0 7 7 0 01-14 0zm-7 0a1.4 1.4 0 011.4-1.4h1.4a1.4 1.4 0 110 2.8H3.4A1.4 1.4 0 012 16zm23.8 0a1.4 1.4 0 011.4-1.4h1.4a1.4 1.4 0 110 2.8h-1.4a1.4 1.4 0 01-1.4-1.4zm-2.87 6.93a1.4 1.4 0 011.98 0l.99.99a1.4 1.4 0 01-1.98 1.98l-.99-.99a1.4 1.4 0 010-1.98zm-15.84 0a1.4 1.4 0 011.98 1.98l-.99.99a1.4 1.4 0 01-1.98-1.98l.99-.99zM16 25.8a1.4 1.4 0 011.4 1.4v1.4a1.4 1.4 0 11-2.8 0v-1.4a1.4 1.4 0 011.4-1.4z"
      /><defs
        ><linearGradient
          id="paint0_linear"
          x1="2"
          y1="2"
          x2="30"
          y2="30"
          gradientUnits="userSpaceOnUse"
          ><stop
            class="transition-all duration-200"
            stop-color="#d4d4d8"
          /><stop
            class="transition-all duration-200"
            offset="1"
            stop-color="#d4d4d8"
          /></linearGradient
        ></defs
      ></svg
    >
    <label class="switch">
      <input type="checkbox" bind:checked on:change={toggle} />
      <span class="slider bg-lime-500 dark:bg-gray-800" />
    </label>
    <svg width="24" height="24"
      ><path
        class="transition-colors duration-200 text-gray-300 dark:bg-gray-700"
        d="M9.353 2.939a1 1 0 01.22 1.08 8 8 0 0010.408 10.408 1 1 0 011.301 1.3A10.003 10.003 0 0112 22C6.477 22 2 17.523 2 12c0-4.207 2.598-7.805 6.273-9.282a1 1 0 011.08.22z"
        fill="currentColor"
      /></svg
    >
  </div>
</div>

<style>
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
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 34px;
  }

  .slider:before {
    position: absolute;
    content: '';
    height: 26px;
    width: 26px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 50%;
  }

  input:checked + .slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
  }
</style>
