/* Variáveis de Cor */
:root {
    --fundo-principal: #121212;
    --fundo-secundario: #1e1e1e;
    --fundo-painel: #2a2a2a;
    --cor-velvet: #E70044; /* Vermelho Velvet Intenso */
    --texto-principal: #ffffff;
    --texto-secundario: #a0a0a0;
}

body {
    background-color: var(--fundo-principal);
    color: var(--texto-principal);
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
}

/* -------------------- HEADER / NAVEGAÇÃO -------------------- */
header {
    background-color: var(--fundo-secundario);
    padding: 15px 5%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 3px solid var(--cor-velvet); /* Destaque Velvet */
}

.logo {
    font-size: 24px;
    font-weight: bold;
    color: var(--cor-velvet);
}

nav a {
    color: var(--texto-principal);
    text-decoration: none;
    margin-left: 25px;
    padding: 5px 10px;
    transition: color 0.3s, background-color 0.3s;
    border-radius: 4px;
}

nav a:hover {
    color: var(--cor-velvet);
}

/* -------------------- MAIN / SEÇÕES -------------------- */
main {
    padding: 30px 5%;
}

hr {
    border: none;
    height: 1px;
    background-color: var(--fundo-painel);
    margin: 40px 0;
}

/* -------------------- CATÁLOGO E FILTROS -------------------- */
.catalogo-area {
    display: flex;
    gap: 30px;
}

.filtros {
    width: 250px;
    padding: 20px;
    background-color: var(--fundo-painel);
    border-radius: 8px;
    height: fit-content;
}

.filtro-grupo {
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 1px dashed var(--fundo-secundario);
}

.filtro-grupo h3 {
    color: var(--cor-velvet);
    margin-top: 0;
    font-size: 16px;
}

.filtros label {
    display: block;
    margin-bottom: 8px;
    font-size: 14px;
    cursor: pointer;
}

.catalogo-lista {
    flex-grow: 1;
}

.grade-jogos {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 25px;
    margin-top: 20px;
}

/* -------------------- CARD DO JOGO (Miniatura) -------------------- */
.game-card {
    background-color: var(--fundo-secundario);
    border-radius: 8px;
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.3s, box-shadow 0.3s;
    border: 1px solid var(--fundo-secundario);
}

.game-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
    border: 1px solid var(--cor-velvet);
}

.game-card img {
    width: 100%;
    height: 150px;
    object-fit: cover;
}

.game-info {
    padding: 15px;
}

.game-info h4 {
    margin-top: 0;
    margin-bottom: 5px;
    font-size: 18px;
    color: var(--texto-principal);
}

.game-tags span {
    display: inline-block;
    background-color: var(--fundo-painel);
    color: var(--cor-velvet);
    font-size: 11px;
    padding: 3px 6px;
    border-radius: 3px;
    margin-right: 5px;
}

.game-price-rating {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
}

.price {
    font-size: 16px;
    font-weight: bold;
    color: var(--cor-velvet);
}

.rating {
    background-color: var(--cor-velvet);
    color: var(--texto-principal);
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 14px;
    font-weight: bold;
}

/* -------------------- FOOTER -------------------- */
.footer-bar {
    background-color: var(--fundo-secundario);
    text-align: center;
    padding: 15px 0;
    font-size: 12px;
    color: var(--texto-secundario);
    margin-top: 50px;
}
