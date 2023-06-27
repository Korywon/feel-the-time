<script lang="ts">
  export let counting: boolean
  export let time: number
  let clientsServed = 0

  const increment = () => {
    setTimeout(() => {
      clientsServed++
      if (counting) increment()
    }, time)
  }

  $: if (counting) increment()
</script>

<div class="flex gap-4 items-center">
  <span class="w-16">{time} ms</span>
  <div>
    Clients served: {clientsServed}
  </div>
</div>
