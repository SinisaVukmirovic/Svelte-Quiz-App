<script>
    export let score;
</script>

<style>
    /* @import url('https://fonts.googleapis.com/css?family=Nova+Mono&display=swap'); */

    .score-board {
        color: #ccc;
        font-size: 1.25rem;
        font-weight: bold;
        text-align: center;
        margin-bottom: 2em;
        padding-bottom: .5em;
        border-bottom: 2px solid #555;
    }
        .score-board span {
            font-family: monospace;
            /* font-variant-numeric: tabular-nums; */
            color: var(--svelte-clr);
            font-size: 3rem;
            font-weight: bold;
            padding: 0 0 0 .25em;
        }

    @media screen and (max-width: 900px) {
        .score-board {
            margin-bottom: 1.5em;
            padding-bottom: .5em;
        }
    }
</style>

<!-- Mark Up -->
<div class="score-board">
    You scored: <span> {score} </span> {score === 1 ? 'point' : 'points'}
</div>