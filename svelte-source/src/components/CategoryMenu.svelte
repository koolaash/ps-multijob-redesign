<script lang="ts">
  import JobCard from './JobCard.svelte';
  import type { Job } from '../types/types';

  export let jobArray: Array<Job> = [];
  export let panelName: string = "";
</script>

<main class="w-[380px] min-h-screen block pt-[20px] select-none glass-effect">
  <div class="text-white px-[28px] pb-4 category-header">
    <p class="category">CATEGORY</p>
    <p class="category-name text-white block mt-[-5px] font-medium capitalize">
      {panelName} Jobs
    </p>
  </div>

  <div class="max-h-screen overflow-y-auto px-[28px] pb-20">
    {#each jobArray as job (job.name)}
      <JobCard name={job.label} nuiName={job.name} nuiRank={job.grade} icon={job.icon} description={job.description}
        salary={job.salary} rank={job.gradeLabel} active={job.active} category={panelName}/>
    {/each}
  </div>
</main>

<style lang="scss">
  .category {
    font-size: 10pt;
    color: var(--color-lightestgrey);
    opacity: 0.8;
    transform: translateZ(0);
    transition: all 0.3s ease;
  }

  .category-name {
    font-size: 15pt;
    letter-spacing: 1px;
    background: linear-gradient(45deg, var(--color-primary), var(--color-secondary));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    position: relative;
    transition: all 0.3s ease;
  }

  .category-name::after {
    content: '';
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--color-primary), var(--color-secondary));
    transition: width 0.3s ease;
  }

  .category-header:hover {
    .category-name::after {
      width: 100%;
    }
    .category {
      transform: translateZ(10px);
      opacity: 1;
    }
  }
</style>