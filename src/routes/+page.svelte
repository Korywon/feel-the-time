<script lang="ts">
  import '../app.css'
  import TimerButton from '../components/timer-button.svelte'
  import TimerCounter from '../components/timer-counter.svelte'

  let timing = false
  const toggleTimer = () => {
    timing = !timing 
  }

  let counting = false
  const toggleCounter = () => {
    counting = !counting 
  }
</script>

<div class="m-4 p-4 flex flex-col gap-4">
  <button
    disabled={timing}
    class="btn btn-primary w-40"
    on:click={toggleTimer}
  >
    Start timer
  </button>
  <div class="flex gap-8">
    <div class="flex-col">
      <TimerButton time={888} {timing} />
      <TimerButton time={760} {timing} />
      <TimerButton time={911} on:done={toggleTimer} {timing} />
    </div>
    <div class="flex-col">
      <TimerButton time={274} {timing} />
      <TimerButton time={263} {timing} />
      <TimerButton time={272} {timing} />
      <TimerButton time={480} {timing} />
    </div>
  </div>
  <button class="btn btn-primary w-40" on:click={toggleCounter}>
    {counting ? 'Stop' : 'Start'} counter
  </button>
  <div class="flex-col gap-8">
    <TimerCounter time={911} {counting} />
    <TimerCounter time={272} {counting} />
  </div>
</div>
