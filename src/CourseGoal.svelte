<script>
    export let courseGoal;

    $: doHighlight = courseGoal.includes('!')
</script>

<style>
    .exclamation-color {
        color: #f00;
    }
</style>

<div>
    <h1 class:exclamation-color={ doHighlight }>{ courseGoal }</h1>
</div>
