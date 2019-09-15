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
                'amazing',
                'ok'
            ]
        },
        {
            question: 'React is...',
            correctAnswer: 1,
            answers: [
                'reactive',
                'not reactive'
            ]
        },
        {
            question: 'Svelte is...',
            correctAnswer: 2,
            answers: [
                'fast',
                'small',
                'all of the above'
            ]
        },
        {
            question: 'Svelte has...',
            correctAnswer: 1,
            answers: [
                'more code',
                'less code',
                'framework code'
            ]
        },
        {
            question: 'The best one is...',
            correctAnswer: 2,
            answers: [
                'Angular',
                'Vue',
                'Svelte',
                'React'
            ]
        },
        {
            question: 'React is a ______________ for React.js',
            correctAnswer: 0,
            answers: [
                'terrible name',
                'adequate name',
                'perfect name',
                'fitting name'
            ]
        },
        {
            question: 'Trully reactive is...',
            correctAnswer: 1,
            answers: [
                'React',
                'Svelte',
                'Vue',
                'Angular'
            ]
        }
    ];

    function checkAnswer(answerText) {
        const isCorrect = quiz[currentQuestion].answers.indexOf(answerText) === 
        quiz[currentQuestion].correctAnswer;

        if (isCorrect) {
            score += 1;
            quiz[currentQuestion].question = 'Correct!';
            
            document.querySelector('.answers').style.display = 'none';
        }
        else {
            quiz[currentQuestion].question = 'Wrong!';
            
            document.querySelector('.answers').style.display = 'none';
        }
        
        if (currentQuestion < quiz.length - 1) {
            setTimeout(function() {
                currentQuestion += 1;
                
                document.querySelector('.answers').style.display = 'grid';
            }, 2000);
        }
        else {
            setTimeout(() => {
                quiz[currentQuestion].question = `Quiz Finished! 
                    You scored ${score}/${quiz.length} points!`;

                document.querySelector('.answers').style.display = 'none';
            }, 4000);            
        }
    }
    
</script>

<style>
	.app  {
        width: 90%;
        max-width: 60rem;
        margin: 5em auto;
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

