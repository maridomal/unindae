<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="assets/style.css">
    <title>Flashcard</title>
</head>
<body>
    <main>
        <section id="container">
            <!-- <article class="cartao">
                <div class="cartao__conteudo">
                    <h3>Programação</h3>
                    <div class="cartao__conteudo__pergunta">
                        <p>O que é JavaScript?</p>
                    </div>
                    <div class="cartao__conteudo__resposta">
                        <p>O JavaScript é uma linguagem de programação</p>
                    </div>
                </div>
            </article> -->
        </section>
    </main>
    <footer>
        <p>Projeto desenvolvido pela Alura, sem fins lucrativos</p>
    </footer>
    <script src="app.js"></script>
    <script src="perguntas.js"></script>
</body>
</html>
:root {
    --text-color: #DBE4EF;
    --card-front-color: #144480;
    --card-back-color: #00F4BF;
}

body {
    background: url('img/bg-desktop.webp');
    font-family: Bai Jamjuree;
}

#container {
    display: flex; 
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 4rem;
    gap: 3rem;
}

.cartao {
    margin: 1rem 1rem;
    height: 20rem;
    flex-grow: 1;
    flex-basis: calc(33% - 6rem);
}

.cartao__conteudo {
    background-color: var(--card-front-color);
    text-align: center;
    /* background-color: aquamarine; */
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 300ms ease-in-out;
}

.cartao__conteudo h3 {
    color: var(--text-color);
    border: 1px solid var(--text-color);
    text-align: left;
    padding: 0.5rem;
    position: absolute;
    margin: 0.6rem;
    border-radius: 0.6rem;
    font-size: 1vw;
    backface-visibility: hidden;
}

.cartao__conteudo p {
    margin-top: 1rem;
    padding: 2rem;
    margin-top: 4rem;
    font-size: 1.4vw;
}

.cartao__conteudo__pergunta p {
    color: var(--text-color);
    font-weight: 500;
}

.cartao__conteudo__resposta p {
    color: var(--card-back-color);
    font-weight: 700;
}

.cartao.active .cartao__conteudo {
    transform: rotateY(180deg);
}

.cartao__conteudo__pergunta,
.cartao__conteudo__resposta {
    backface-visibility: hidden;
    position: absolute;
    height: 100%;
    width: 100%;
    box-sizing: border-box;
}

.cartao__conteudo__resposta {
    transform: rotateY(180deg);
    background-color: rgba(0, 244, 191, 0.2);
    border: 4px solid var(--card-back-color);
}

footer {
    background-color: black;
    color: white;
    position: fixed;
    bottom: 0;
    width: 100%;
    height: 2rem;
}

footer p {
    text-align: center;
    font-size: 0.6rem;
    margin-top: 0.5rem;
}

@media (max-width: 560px) {
    
    body {
        background: url('img/bg-mobile.webp'), no-repeat cover;
    }

    .cartao {
        flex: 1 0 calc(100% - 1rem)
    }

    .cartao__conteudo h3 {
        font-size: 3vw;
    }

    .cartao__conteudo p {
        font-size: 3.8vw;
    }
}
criaCartao(
    'Programação',
    'O que é Python?',
    'O Python é uma linguagem de programação'
)

criaCartao(
    'Geografia',
    'Qual a capital da França?',
    'A capital da França é Paris'
)

criaCartao(
    'Programação',
    'O que é uma função?',
    'Uma função é um bloco de código que executa alguma tarefa'
)

criaCartao(
    'Lingua inglesa',
    'Como se diz oi em Inglês?',
    'Oi em ingles é HI (RAI)'
)
function criaCartao(categoria, pergunta, resposta) {
    let container = document.getElementById('container')
    let cartao = document.createElement('article')
    cartao.className = 'cartao'

    cartao.innerHTML = `
    <div class="cartao__conteudo">
    <h3>${categoria}</h3>
    <div class="cartao__conteudo__pergunta">
        <p>${pergunta}</p>
    </div>
    <div class="cartao__conteudo__resposta">
        <p>${resposta}</p>
    </div>
    </div>
    `

    let respostaEstaVisivel = false

    function viraCartao() {
        respostaEstaVisivel = !respostaEstaVisivel
        cartao.classList.toggle('active', respostaEstaVisivel)
    }
    cartao.addEventListener('click', viraCartao)


    container.appendChild(cartao)

}
