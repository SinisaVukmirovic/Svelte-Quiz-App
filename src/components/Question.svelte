<script>
    export let questionText;
</script>

<style>
    .questions {
        padding: 0 4em;
    }
        .questions h2 {
            color: cornflowerblue;
        }

    @media screen and (max-width: 900px) {
        .questions {
            padding: 0 2em;
        }
    }
</style>

<!-- Mark Up -->
<div class="questions">
    <h2>{questionText}</h2>
</div>