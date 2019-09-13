<script>
    export let score;
</script>

<style>
    .score-board {
        color: #ccc;
        font-size: 1.25rem;
        font-weight: bold;
        text-align: center;
        margin-bottom: 2em;
    }
        .score-board span {
            color: var(--svelte-clr);
            font-size: 3rem;
            font-weight: bold;
        }
</style>

<!-- Mark Up -->
<div class="score-board">You Scored: <span>{score}</span> points!</div>