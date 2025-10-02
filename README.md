// Dados Fictícios de Jogos (Simulando informações de Epic/Ubisoft/UE5)
const gamesData = [
    {
        id: 1,
        title: "Black Myth: Wukong",
        image: "https://via.placeholder.com/250x150/E70044/FFFFFF?text=WUKONG",
        loja: "epic",
        engine: "ue5",
        price: 249.99,
        rating: 9.2,
        url: "https://store.epicgames.com/",
        popularidade: "Mais Aguardado"
    },
    {
        id: 2,
        title: "Assassin's Creed Shadows",
        image: "https://via.placeholder.com/250x150/1e1e1e/E70044?text=AC+SHADOWS",
        loja: "ubisoft",
        engine: "outros",
        price: 349.99,
        rating: 8.5,
        url: "https://store.ubisoft.com/",
        popularidade: "Lançamento"
    },
    {
        id: 3,
        title: "Ark: Survival Ascended",
        image: "https://via.placeholder.com/250x150/4400E7/FFFFFF?text=ARK+UE5",
        loja: "epic",
        engine: "ue5",
        price: 150.00,
        rating: 7.9,
        url: "https://store.epicgames.com/",
        popularidade: "Em Acesso"
    },
    {
        id: 4,
        title: "Star Wars Outlaws",
        image: "https://via.placeholder.com/250x150/1e1e1e/E70044?text=SW+OUTLAWS",
        loja: "ubisoft",
        engine: "outros",
        price: 320.00,
        rating: 0, // Pré-venda
        url: "https://store.ubisoft.com/",
        popularidade: "Pré-venda"
    },
    {
        id: 5,
        title: "Alan Wake 2",
        image: "https://via.placeholder.com/250x150/1e1e1e/FFFFFF?text=ALAN+WAKE+2",
        loja: "epic",
        engine: "ue4", // Exemplo de um jogo Epic que não é UE5
        price: 199.99,
        rating: 9.0,
        url: "https://store.epicgames.com/",
        popularidade: "Sucesso Crítico"
    }
];

const listaJogosContainer = document.getElementById('lista-jogos');
const destaqueCarrossel = document.getElementById('destaque-carrossel');
const filtrosCheckboxes = document.querySelectorAll('.filtros input[type="checkbox"]');

// Função para criar o card de um jogo
function createGameCard(game) {
    const card = document.createElement('div');
    card.className = 'game-card';
    card.setAttribute('data-loja', game.loja);
    card.setAttribute('data-engine', game.engine);
    card.onclick = () => window.open(game.url, '_blank'); // Redireciona para a loja

    let ratingDisplay = game.rating > 0 ? `<span class="rating">${game.rating}</span>` : '<span class="rating">N/A</span>';
    let engineTag = game.engine === 'ue5' ? `<span class="ue5-tag">UE5</span>` : `<span>${game.engine.toUpperCase()}</span>`;

    card.innerHTML = `
        <img src="${game.image}" alt="${game.title}">
        <div class="game-info">
            <h4>${game.title}</h4>
            <div class="game-tags">
                <span class="loja-tag">${game.loja.toUpperCase()}</span>
                ${engineTag}
            </div>
            <div class="game-price-rating">
                <span class="price">R$ ${game.price.toFixed(2).replace('.', ',')}</span>
                ${ratingDisplay}
            </div>
        </div>
    `;
    return card;
}

// Função para renderizar todos os jogos no catálogo
function renderGames(games) {
    listaJogosContainer.innerHTML = '';
    games.forEach(game => {
        listaJogosContainer.appendChild(createGameCard(game));
    });
}

// Função de filtragem
function applyFilters() {
    const filtrosAtivos = {
        lojas: [],
        engines: []
    };

    filtrosCheckboxes.forEach(checkbox => {
        if (checkbox.checked) {
            const [tipo, valor] = checkbox.dataset.filtro.split('-');
            if (tipo === 'loja') {
                filtrosAtivos.lojas.push(valor);
            } else if (tipo === 'engine') {
                filtrosAtivos.engines.push(valor);
            }
        }
    });

    const jogosFiltrados = gamesData.filter(game => {
        const lojaMatch = filtrosAtivos.lojas.length === 0 || filtrosAtivos.lojas.includes(game.loja);
        const engineMatch = filtrosAtivos.engines.length === 0 || filtrosAtivos.engines.includes(game.engine);
        return lojaMatch && engineMatch;
    });

    renderGames(jogosFiltrados);
}

// Adiciona listener para os filtros
filtrosCheckboxes.forEach(checkbox => {
    checkbox.addEventListener('change', applyFilters);
});

// Renderiza o jogo de destaque (o primeiro UE5)
function renderDestaque() {
    const destaqueGame = gamesData.find(g => g.engine === 'ue5');
    if (destaqueGame) {
        destaqueCarrossel.innerHTML = `
            <div class="destaque-card" style="background-image: url('${destaqueGame.image.replace('250x150', '900x400')}')">
                <div class="destaque-overlay">
                    <span class="velvet-tag">UNREAL ENGINE 5</span>
                    <h2>${destaqueGame.title}</h2>
                    <p class="popularidade-tag">${destaqueGame.popularidade}</p>
                    <p>Nota: ${destaqueGame.rating} | Preço: R$ ${destaqueGame.price.toFixed(2).replace('.', ',')}</p>
                    <a href="${destaqueGame.url}" target="_blank" class="btn-velvet">IR PARA A LOJA OFICIAL</a>
                </div>
            </div>
        `;
    }
}

// Estilização extra para o destaque
const style = document.createElement('style');
style.innerHTML = `
    .destaque-card {
        width: 100%;
        height: 400px;
        background-size: cover;
        background-position: center;
        border-radius: 8px;
        position: relative;
    }
    .destaque-overlay {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        padding: 30px;
        background: linear-gradient(to top, rgba(18, 18, 18, 0.9), rgba(18, 18, 18, 0));
        color: white;
        border-bottom-left-radius: 8px;
        border-bottom-right-radius: 8px;
    }
    .destaque-overlay h2 {
        color: var(--cor-velvet);
        margin-top: 5px;
        font-size: 36px;
    }
    .velvet-tag {
        background-color: var(--cor-velvet);
        color: white;
        padding: 5px 10px;
        border-radius: 5px;
        font-weight: bold;
        font-size: 14px;
        display: inline-block;
        margin-bottom: 10px;
    }
    .btn-velvet {
        display: inline-block;
        background-color: var(--cor-velvet);
        color: white;
        padding: 10px 20px;
        text-decoration: none;
        border-radius: 5px;
        font-weight: bold;
        margin-top: 15px;
        transition: opacity 0.3s;
    }
    .btn-velvet:hover {
        opacity: 0.9;
    }
`;
document.head.appendChild(style);


// Inicialização
document.addEventListener('DOMContentLoaded', () => {
    renderDestaque();
    renderGames(gamesData);
});
