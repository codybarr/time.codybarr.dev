<script>
  import { utcToZonedTime, format } from 'date-fns-tz'

  const DATE_FORMAT = 'EEE MMMM d, Y'
  const TIME_FORMAT = 'h:mm:ss aaa'
  const TIMEZONE_FORMAT = 'zzzz'

  export let date
  export let timezone

  $: zonedDate = timezone ? utcToZonedTime(date, timezone) : date
  $: formattedDate = format(zonedDate, DATE_FORMAT)
  $: formattedTime = format(zonedDate, TIME_FORMAT)
  $: formattedTimezone = format(zonedDate, TIMEZONE_FORMAT, {
    timeZone: timezone,
  })
</script>

<div
  class="date-card text-center overflow-hidden grid grid-cols-1 grid-rows-2 shadow-lg text-black rounded-md mt-5 w-full max-w-md bg-white dark:bg-gray-700 dark:text-white"
>
  <div class="row-span-2 p-5">
    <p class="text-3xl font-bold">{formattedTime}</p>
    <p class="text-xl mt-4">{formattedDate}</p>
  </div>
  <div
    class="p-5 bg-gray-700 text-white dark:bg-lime-500 dark:text-gray-700 text-center text-xl"
  >
    {formattedTimezone}
  </div>
</div>

<style>
  .date-card {
    font-family: 'Questrial';
  }
</style>
