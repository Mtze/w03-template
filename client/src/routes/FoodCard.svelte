<script lang="ts">
    import Icon from "@iconify/svelte";
    import type { Meal } from "$lib/types";

    export let meal: Meal;
</script>

<div class="food-card">
    <h2>{meal.name}</h2>
    <div class="dish-type">{meal.dish_type}</div>

    <div class="section">
        <h3>Labels</h3>
        <div class="label-section">
            {#if meal.labels && meal.labels.length > 0}
                {#each meal.labels as label}
                    {#if label.includes("vegan") || label.includes("vegetarian")}
                        <span class="label diet-label">
                            <Icon icon="mdi:leaf" />
                            {label}
                        </span>
                    {:else if label.includes("beef") || label.includes("pork") || label.includes("chicken")}
                        <span class="label meat-label">
                            <Icon icon="mdi:food-steak" />
                            {label}
                        </span>
                    {:else}
                        <span class="label allergen-label">
                            <Icon icon="mdi:information-outline" />
                            {label}
                        </span>
                    {/if}
                {/each}
            {:else}
                <span class="no-additives">No labels provided</span>
            {/if}
        </div>
    </div>
</div>
