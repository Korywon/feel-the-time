<script lang="ts">
  import { createEventDispatcher } from 'svelte'
  import Fa from 'svelte-fa'
  import {
    faCheck, faCircleNotch, faEllipsis 
  } from '@fortawesome/free-solid-svg-icons'

  export let time: number
  export let timing = false
  let done = false
  const dispatch = createEventDispatcher<{done: void}>() 

  $: if (timing) {
    setTimeout(() => {
      done = true
      timing = false
      dispatch('done')
    }, time)
  }
</script>

<div class="flex gap-4 items-center">
  <span class="w-16">{time} ms</span>
  <div>
    {#if timing}
      <Fa class="text-yellow-400" icon={faCircleNotch} spin />
    {:else if done}
      <Fa class="text-green-400" icon={faCheck} />
    {:else}
      <Fa class="text-blue-400" icon={faEllipsis} />
    {/if}
  </div>
</div>
