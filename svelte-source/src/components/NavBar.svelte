<script lang="ts">
  import NavItem from './atoms/NavItem.svelte';
  import PanelStore from '../stores/PanelStore';
  import type { side } from '../types/types';

  export let side: side;

  const { panelActive, panels } = PanelStore;
</script>

<nav class="w-[80px] min-h-screen nav flex flex-col z-10 glass-effect">
  <div class="ps-logo w-full h-[80px]"/>
  {#each $panels as item}
    <NavItem name={item.name} isActive={item.name == $panelActive} icon={item.icon} {side}/>
  {/each}
</nav>

<style>
  .nav {
    border-left: 1px solid rgba(255, 255, 255, 0.1);
  }
</style>