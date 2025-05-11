<script lang="ts">
  export let icon: any = null;
  export let detail: string;
  export let value: string | number;
  export let svgSize: string;
</script>

<div class="flex flex-1 flex-col items-center gap-2 border rounded-lg border-[rgba(255,255,255,0.1)] 
  pt-[14px] pb-[14px] transition-all duration-300 hover:border-[var(--color-primary)] 
  hover:shadow-[0_0_10px_rgba(14,165,233,0.2)]">
  <div class="w-full flex justify-center text-[var(--color-primary)]">
    <div class={svgSize}>
      <svelte:component this={icon}/>
    </div>
  </div>
  <div class="text-center">
    <p class="text-xs text-[var(--color-lightgrey)]">
      {detail}:
      <span class="text-[var(--color-primary)]">
        {value}
      </span>
    </p>
  </div>
</div>