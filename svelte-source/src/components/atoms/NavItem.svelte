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

<div class={"navitem w-full h-[60px] flex justify-center items-center cursor-pointer transition-all duration-500 "+
  (side == "left" ? "border-l-4 " : "border-r-4 ")+
  (isActive ? 
    side == "left" ? 
      "border-l-[var(--color-primary)] bg-[rgba(15,23,42,0.8)] shadow-[inset_0_0_20px_rgba(56,189,248,0.2)] animate-glow": 
      "border-r-[var(--color-primary)] bg-[rgba(15,23,42,0.8)] shadow-[inset_0_0_20px_rgba(56,189,248,0.2)] animate-glow"
  : side == "left" ? 
      "border-l-transparent hover:border-l-[var(--color-secondary)]": 
      "border-r-transparent hover:border-r-[var(--color-secondary)]")}
  on:click={() => navItemClicked(name)}
>
  <div class="icon transition-all duration-300 transform hover:scale-110 hover:rotate-12">
    <svelte:component this={icon} color={isActive ? "var(--color-primary)" : "var(--color-grey)"}/>
  </div>
</div>

<style>
  .icon {
    width: 40%;
    color: var(--color-lightestgrey);
  }
  .navitem {
    position: relative;
    overflow: hidden;
  }
  .navitem:hover {
    background-color: rgba(15, 23, 42, 0.8);
  }
  .navitem:hover .icon {
    transform: scale(1.1) translateY(-2px);
  }
  .navitem::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(45deg, transparent, rgba(56, 189, 248, 0.1), transparent);
    transform: translateX(-100%);
    transition: transform 0.6s ease;
  }
  .navitem:hover::after {
    transform: translateX(100%);
  }
  
  @keyframes glow {
    0% { box-shadow: inset 0 0 10px rgba(56, 189, 248, 0.2); }
    50% { box-shadow: inset 0 0 20px rgba(56, 189, 248, 0.4); }
    100% { box-shadow: inset 0 0 10px rgba(56, 189, 248, 0.2); }
  }
  
  .animate-glow {
    animation: glow 2s infinite;
  }
</style>