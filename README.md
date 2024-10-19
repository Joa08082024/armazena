<!DOCTYPE html>
<html>
  <head>
    <title>Formulário de Ofertas</title>
  </head>
  <body>
    <form id="ofertasForm">
      <label for="classe">Classe:</label>
      <select id="classe" name="classe" required>
        <option value="OFERTASCORDEIRIHOSDECRISTO">Cordeirinhos de Cristo</option>
        <option value="OFERTASESTRELADAMANHA">Estrela da Manhã</option>
        <option value="OFERTASHEROISDAFE">Heróis da Fé</option>
        <option value="OFERTASLIRIODOSVALES">Lírio dos Vales</option>
        <option value="OFERTASSEMENTINHAS">Sementinhas</option>
      </select><br><br>

      <label for="data">Data da Oferta:</label>
      <input type="date" id="data" name="data" required><br><br>

      <label for="valor">Valor da Oferta:</label>
      <input type="number" id="valor" name="valor" required><br><br>

      <button type="submit">Enviar</button>
    </form>

    <script>
      document.getElementById('ofertasForm').addEventListener('submit', function(e) {
        e.preventDefault();

        const classe = document.getElementById('classe').value;
        const data = document.getElementById('data').value;
        const valor = document.getElementById('valor').value;

        fetch('https://script.google.com/macros/s/AKfycbwj7CGDOvO2lHsKkhJUnzj8R0n5_yIh1TcaithWYNk823VJNoOlItAAxkxIDWduz8Os/exec', {
          method: 'POST',
          body: JSON.stringify({ classe, data, valor }),
          headers: {
            'Content-Type': 'application/json'
          }
        })
        .then(response => response.json())
        .then(data => {
          console.log(data);
          alert('Dados enviados com sucesso!');
        })
        .catch(error => {
          console.error('Error:', error);
          alert('Erro ao enviar dados.');
        });
      });
    </script>
  </body>
</html>
