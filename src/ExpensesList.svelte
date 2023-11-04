<script>
    import Title from './Title.svelte';
    import Expense from './Expense.svelte'
    import {fly} from "svelte/transition";
    import {flip} from "svelte/animate";
    //variable
    export let expenses = [];
</script>

<style>
    h2 {
        text-transform: capitalize;
    }
</style>


<section>
    <Title title="expense list"/>
    <ul>
        {#each expenses as expense, index (expense.id)}
            <div in:fly={{x:200, delay:index*700}} out:fly={{x: -200}} animate:flip>
                <Expense {...expense}/>
            </div>
            {:else}
            <h2>No Expenses in the list yet</h2>
        {/each}
    </ul>
</section>