<script>
	import Header from './components/Header.svelte';
    import Score from './components/Score.svelte';
    import Question from './components/Question.svelte';
    import Answer from './components/Answer.svelte';
    
    let score = 0;

    let currentQuestion = 0;

    const quiz = [
        {
            question: 'Svelte is... ?',
            correctAnswer: 0,
            answers: [
                'The Best',
                'Bad',
                'OK',
                'Meh'
            ]
        },
    ];
</script>

<style>
	.app  {
        width: 90%;
        max-width: 60rem;
        margin: 3em auto;
        padding: 1em 3em;
        background-color: #222;
    }

    .answers {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        justify-content: space-evenly;
        grid-gap: 2em;
        margin: 2em auto;
    }
</style>

<!-- Mark Up -->
<Header />

<div class="app">

    <Score {score}/>

    <Question questionText={quiz[currentQuestion].question}/>

    <div class="answers">
        {#each quiz[currentQuestion].answers as answer}
            <Answer answerText={answer}/>
        {/each}
    </div>

</div>

