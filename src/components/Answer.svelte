<script>
    export let answerText;
    export let checkAnswer;
</script>

<style>
    
</style>

<!-- Mark Up -->
<button on:click={() => checkAnswer(answerText)}>{answerText}</button>