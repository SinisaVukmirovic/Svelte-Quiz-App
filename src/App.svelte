<script>
	import Header from './components/Header.svelte';
    import Score from './components/Score.svelte';
    import Question from './components/Question.svelte';
    import Answer from './components/Answer.svelte';
    
    let score = 0;

    let currentQuestion = 0;

    const quiz = [
        {
            question: 'Svelte is...',
            correctAnswer: 0,
            answers: [
                'the Best',
                'mehh'
            ]
        },
        {
            question: 'React is...',
            correctAnswer: 0,
            answers: [
                'not reactive',
                'small',
                'fast'
            ]
        },
        {
            question: 'The best one is...',
            correctAnswer: 0,
            answers: [
                'Svelte',
                'Angular',
                'Vue',
                'React'
            ]
        },
        {
            question: 'React is a __________ for React.js',
            correctAnswer: 0,
            answers: [
                'terrible name',
                'adequate name',
                'fitting name',
            ]
        },
        {
            question: 'Trully reactive is...',
            correctAnswer: 0,
            answers: [
                'Svelte',
                'Vue',
                'React',
                'Angular'
            ]
        }
    ];

    function checkAnswer(answerText) {
        const isCorrect = quiz[currentQuestion].answers.indexOf(answerText) === 
        quiz[currentQuestion].correctAnswer;

        if (isCorrect) {
            score += 1;
        }

        currentQuestion += 1;

        if (currentQuestion === quiz.length) {
            currentQuestion = 0;
            score = 0;
        }

    }
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

    @media screen and (max-width: 900px) {
        .app  {
            width: 90%;
            max-width: 60rem;
            margin: 3em auto;
            padding: 1em;
            background-color: #222;
        }

        .answers {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            justify-content: space-evenly;
            grid-gap: 1em;
            margin: 2em auto;
        }
    }

    @media screen and (max-width: 567px) {
        .answers {
            grid-template-columns: repeat(1, 1fr);
            grid-gap: 1em;
            margin: 1em auto;
        }
    }
</style>

<!-- Mark Up -->
<Header />

<div class="app">

    <Score {score}/>

    <Question questionText={quiz[currentQuestion].question}/>

    <div class="answers">
        {#each quiz[currentQuestion].answers as answer}
            <Answer answerText={answer} checkAnswer={checkAnswer} />
        {/each}
    </div>

</div>

