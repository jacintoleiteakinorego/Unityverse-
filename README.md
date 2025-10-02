# Unityverse-<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unityverse - Seu Hub de Jogos Unificado</title>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
    <header>
        <div class="logo">Unityverse</div>
        <nav>
            <a href="#">Loja</a>
            <a href="#">Comunidade</a>
            <a href="#">Novidades UE5</a>
            <a href="#">Minha Conta</a>
        </nav>
    </header>

    <main>
        <section id="destaque" class="destaque-area">
            <h1>Lançamentos em Destaque</h1>
            <div id="destaque-carrossel" class="carrossel">
                </div>
        </section>

        <hr>

        <section class="catalogo-area">
            <aside class="filtros">
                <h2>Filtrar Catálogo</h2>
                <div class="filtro-grupo">
                    <h3>Loja</h3>
                    <label><input type="checkbox" data-filtro="loja-epic"> Epic Games Store</label>
                    <label><input type="checkbox" data-filtro="loja-ubisoft"> Ubisoft Store</label>
                </div>
                <div class="filtro-grupo">
                    <h3>Engine</h3>
                    <label><input type="checkbox" data-filtro="engine-ue5"> Unreal Engine 5</label>
                    <label><input type="checkbox" data-filtro="engine-ue4"> Unreal Engine 4</label>
                </div>
                </aside>

            <div class="catalogo-lista">
                <h2>Catálogo Unificado</h2>
                <div id="lista-jogos" class="grade-jogos">
                    </div>
            </div>
        </section>
    </main>

    <footer class="footer-bar">
        &copy; 2025 Unityverse - Portal de Jogos Agregados.
    </footer>

    <script src="script.js"></script>
</body>
</html>
