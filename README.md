<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LM JOGOS</title>
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background: linear-gradient(to bottom, #ffcc00, #ff0066);
      color: white;
      text-align: center;
    }
    header {
      padding: 2rem 1rem;
    }
    h1 {
      font-size: 3rem;
      margin-bottom: 0.5rem;
    }
    .btn-download {
      background: #00ffcc;
      color: #000;
      padding: 1rem 2rem;
      border: none;
      border-radius: 10px;
      font-size: 1.2rem;
      cursor: pointer;
      margin-top: 1rem;
    }
    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      padding: 2rem;
    }
    .gallery a img {
      width: 200px;
      height: 120px;
      object-fit: cover;
      border-radius: 10px;
    }
    .native-ads {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin: 2rem auto;
      max-width: 800px;
    }
    .native-ad {
      background: #fff;
      color: #000;
      border-radius: 10px;
      width: 200px;
      padding: 10px;
      text-align: center;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }
    .native-ad img {
      width: 100%;
      border-radius: 10px;
    }
    .native-ad h4 {
      margin: 10px 0 5px;
      font-size: 1rem;
    }
    .native-ad p {
      font-size: 0.9rem;
    }
    .native-ad a {
      display: inline-block;
      margin-top: 8px;
      padding: 6px 10px;
      background: #00ffcc;
      border-radius: 5px;
      text-decoration: none;
      color: #000;
      font-weight: bold;
    }
    footer {
      margin-top: 3rem;
      padding: 1rem;
      background-color: rgba(0,0,0,0.2);
    }
  </style>
</head>
<body>
  <header>
    <h1>LM JOGOS</h1>
    <p>Bem-vindo ao seu universo de jogos!</p>
    <button class="btn-download">Baixar App</button>
  </header>

  <!-- GALERIA DE JOGOS -->
  <section class="gallery">
    <a href="https://jogo1.com" target="_blank">
      <img src="https://via.placeholder.com/200x120.png?text=Jogo+1" alt="Jogo 1">
    </a>
    <a href="https://jogo2.com" target="_blank">
      <img src="https://via.placeholder.com/200x120.png?text=Jogo+2" alt="Jogo 2">
    </a>
    <a href="https://jogo3.com" target="_blank">
      <img src="https://via.placeholder.com/200x120.png?text=Jogo+3" alt="Jogo 3">
    </a>
    <a href="https://jogo4.com" target="_blank">
      <img src="https://via.placeholder.com/200x120.png?text=Jogo+4" alt="Jogo 4">
    </a>
  </section>

  <!-- ANÚNCIOS NATIVOS INSTAL -->
  <h2>Anúncios Recomendados</h2>
  <div class="native-ads" id="nativeAds"></div>

  <script>
    fetch('http://ads.instal.com/api/v1/servead/native?id=5476&slots_n=4')
      .then(response => response.json())
      .then(data => {
        const container = document.getElementById('nativeAds');
        data.ads.forEach(ad => {
          const div = document.createElement('div');
          div.className = 'native-ad';
          div.innerHTML = `
            <img src="${ad.icon_url}" alt="${ad.title}">
            <h4>${ad.title}</h4>
            <p>${ad.description}</p>
            <a href="${ad.click_url}" target="_blank">Baixar</a>
          `;
          container.appendChild(div);
        });
      })
      .catch(error => {
        console.error('Erro ao carregar anúncios:', error);
      });
  </script>

  <footer>
    <p>Siga a LM JOGOS nas redes sociais!</p>
  </footer>
</body>
</html>
