<script lang="ts">
  import PanelStore from "../../stores/PanelStore";
  import type { side } from '../../types/types';

  export let icon: any;
  export let isActive: boolean;
  export let name: string;
  export let side: side;

  function navItemClicked(item: string): void {
    if (isActive) {
      PanelStore.setActive("");
    } else {
      PanelStore.setActive(item);
    }
  }
</script>

<div class={"navitem w-full h-[60px] flex justify-center items-center cursor-pointer transition-all duration-300 "+
  (side == "left" ? "border-l-4 " : "border-r-4 ")+
  (isActive ? 
    side == "left" ? 
      "border-l-[var(--color-primary)] bg-[var(--color-darkest)] shadow-[inset_0_0_15px_rgba(14,165,233,0.2)]": 
      "border-r-[var(--color-primary)] bg-[var(--color-darkest)] shadow-[inset_0_0_15px_rgba(14,165,233,0.2)]"
  : side == "left" ? 
      "border-l-transparent hover:border-l-[var(--color-secondary)]": 
      "border-r-transparent hover:border-r-[var(--color-secondary)]")}
  on:click={() => navItemClicked(name)}
>
  <div class="icon transition-all duration-300">
    <svelte:component this={icon} color={isActive ? "var(--color-primary)" : "var(--color-grey)"}/>
  </div>
</div>

<style>
  .icon {
    width: 40%;
    color: var(--color-lightestgrey);
  }
  .navitem:hover {
    background-color: var(--color-darkest);
  }
  .navitem:hover .icon {
    transform: scale(1.1);
  }
</style>