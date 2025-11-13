<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>HEADSHOP DO TIO K</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background: linear-gradient(135deg, #000000, #0a0a33);
      color: white;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 30px;
      perspective: 1000px;
    }

    .logo {
      font-size: 3rem;
      font-weight: 800;
      color: #00aaff;
      text-shadow: 0 0 25px #00aaff;
      margin-bottom: 25px;
      animation: spin 6s infinite linear;
      transform-style: preserve-3d;
    }

    @keyframes spin {
      0% { transform: rotateY(0deg); }
      100% { transform: rotateY(360deg); }
    }

    .product {
      background: rgba(0, 0, 0, 0.8);
      border: 1px solid #00aaff;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0, 170, 255, 0.3);
      padding: 20px;
      margin: 10px 0;
      width: 300px;
      transform: rotateY(3deg);
      transition: all 0.3s ease;
    }

    .product:hover {
      transform: scale(1.05) rotateY(0deg);
      box-shadow: 0 0 30px rgba(0, 170, 255, 0.6);
    }

    .product h2 {
      font-size: 1.2rem;
      margin-bottom: 10px;
      color: #00aaff;
    }

    .product p {
      font-size: 0.95rem;
      margin-bottom: 8px;
    }

    .controls {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 10px;
    }

    input[type="number"] {
      width: 70px;
      padding: 5px;
      border-radius: 8px;
      border: none;
      text-align: center;
      outline: none;
      font-weight: bold;
    }

    button {
      background: #00aaff;
      color: white;
      border: none;
      border-radius: 10px;
      padding: 8px 12px;
      cursor: pointer;
      font-weight: bold;
      transition: 0.3s;
    }

    button:hover {
      background: #0077cc;
      box-shadow: 0 0 10px #00aaff;
    }
  </style>
</head>
<body>
  <div class="logo">HEADSHOP DO TIO K</div>

  <div id="produtos"></div>

  <script>
    const produtos = [
      { nome: "Pré bolado normal", preco: "R$10,00", atacado: "R$8,00 (20+)" },
      { nome: "Tabaco acrema", preco: "R$20,00" },
      { nome: "Tabaco Amsterdam", preco: "R$20,00" },
      { nome: "Cuia", preco: "R$10,00" },
      { nome: "Tesoura lisa", preco: "R$8,00" },
      { nome: "Tesoura da garça", preco: "R$25,00" },
      { nome: "Tesoura de aço", preco: "R$25,00" },
      { nome: "Seda Goru Sadhu Longa", preco: "R$7,00" },
      { nome: "Seda O2 Slim", preco: "R$3,00 (2 por 5)" },
      { nome: "Seda Zomo Slim", preco: "R$3,00 (2 por 5)" },
      { nome: "Slick To Na B (5g)", preco: "R$13,00" },
      { nome: "Maçarico", preco: "R$20,00" },
      { nome: "Kit básico", preco: "R$85,00" },
      { nome: "Case", preco: "R$33,00" },
      { nome: "Piteira Mega Large Adesivo", preco: "R$6,00" }
    ];

    const container = document.getElementById("produtos");
    const numeroWhatsApp = "5511978488902";

    produtos.forEach(produto => {
      const div = document.createElement("div");
      div.className = "product";

      div.innerHTML = `
        <h2>${produto.nome}</h2>
        <p><strong>Preço:</strong> ${produto.preco}</p>
        ${produto.atacado ? `<p><strong>Atacado:</strong> ${produto.atacado}</p>` : ""}
        <div class="controls">
          <input type="number" min="1" value="1" id="qtd-${produto.nome.replace(/\s+/g, '-')}">
          <button onclick="finalizarCompra('${produto.nome}', 'qtd-${produto.nome.replace(/\s+/g, '-')}')">
            Comprar
          </button>
        </div>
      `;
      container.appendChild(div);
    });

    function finalizarCompra(nome, inputId) {
      const qtd = document.getElementById(inputId).value;
      const mensagem = encodeURIComponent(`Olá! Quero confirmar meu pedido na HEADSHOP DO TIO K:\n\nProduto: ${nome}\nQuantidade: ${qtd}\n\nPode me passar a forma de pagamento?`);
      window.open(`https://wa.me/${"5511978488902"}?text=${mensagem}`, "_blank");
    }
  </script>
</body>
</html>
