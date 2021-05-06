<script>
  import { onMount } from 'svelte'
  import { theme } from './store.js'

  import ThemeSwitcher from './components/ThemeSwitcher.svelte'
  import DateCard from './components/DateCard.svelte'
  const TIMEZONES = { PST: 'America/Los_Angeles' }

  let date = new Date()

  onMount(() => {
    const interval = setInterval(() => {
      date = new Date()
    }, 1000)

    return () => {
      clearInterval(interval)
    }
  })
</script>

<div class:dark={$theme === 'dark'} class="min-h-screen">
  <main
    class="flex flex-col items-center pt-8 min-h-screen w-full bg-sepia dark:bg-gray-900 dark:text-white"
  >
    <ThemeSwitcher />
    <DateCard {date} />
    <DateCard {date} timezone={TIMEZONES.PST} />
  </main>
</div>

<style>
  :global(html, body) {
    min-height: 100vh;
  }
</style>
