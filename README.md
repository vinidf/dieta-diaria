# Minha Dieta

App web estático em português do Brasil para acompanhar uma dieta diária sem backend.

## Recursos

- Quantidade configurável de 1 a 12 refeições por dia.
- Nome e horário configuráveis para cada refeição.
- Itens nutricionais configuráveis por refeição.
- Checkbox por item.
- Totais automáticos de calorias, carboidratos, proteínas, fibras e gorduras dos itens consumidos.
- Indicadores visuais no topo.
- Menu superior organizado em Dia, Dieta e Dados.
- Adição rápida em modal para o dia atual.
- Busca de produto por código de barras usando Open Food Facts.
- Leitura por câmera quando o navegador oferece `BarcodeDetector`.
- Preenchimento manual como alternativa quando a câmera ou o produto não estiver disponível.
- Edição e exclusão de itens do dia atual.
- Versionamento de cada dia no `localStorage`.
- Histórico de versões diárias.
- Exportação/importação de backup JSON.
- Importação e cadastro/edição da dieta-base em JSON.
- Layout responsivo para celular, incluindo a configuração de refeições.

## Código de barras

A adição rápida permite informar o código manualmente ou usar a câmera do dispositivo quando suportado pelo navegador. A consulta nutricional usa a API pública do Open Food Facts. Os dados retornados são usados como ponto de partida e devem ser conferidos no rótulo do produto antes de salvar.

Os valores nutricionais obtidos nessa consulta são apresentados como referência por 100 g/ml. O código de barras pode ser armazenado junto ao item adicionado.

O código de barras é enviado ao Open Food Facts somente quando a busca de produto é utilizada. A consulta é feita diretamente do navegador, sem backend próprio.

## Configuração das refeições

Na opção **Configurar refeições**, a pessoa define o nome e o horário de cada refeição, pode adicionar ou remover refeições e pode cadastrar alimentos na dieta-base. A interface usa um layout responsivo para evitar que os campos ultrapassem a largura da tela em celulares.

## Formato JSON da dieta

A dieta usa `schemaVersion: 2` e aceita de 1 a 12 refeições. Cada refeição define seu próprio nome e horário.

```json
{
  "schemaVersion": 2,
  "name": "Minha dieta",
  "meals": [
    {
      "id": "refeicao-1",
      "name": "Café da manhã",
      "time": "08:00",
      "items": [
        {
          "id": "ovo",
          "name": "Ovo",
          "calories": 70,
          "carbs": 0.4,
          "protein": 6.3,
          "fiber": 0,
          "fat": 4.8
        }
      ]
    },
    {
      "id": "refeicao-2",
      "name": "Almoço",
      "time": "12:00",
      "items": []
    }
  ]
}
```

Os valores nutricionais são referentes à porção representada pelo item. Para produtos encontrados por código de barras, o app inicialmente apresenta os valores informados pelo Open Food Facts por 100 g/ml.

## Armazenamento

A chave `dietaDiaria.v2` do `localStorage` guarda a dieta-base e o histórico por data. Cada alteração gera uma nova versão do dia.

## Privacidade e direitos

Não há conta, backend, analytics ou envio de registros da dieta para um servidor próprio. Os dados registrados pelo usuário ficam no navegador. O backup exportado contém a estrutura da dieta e os registros locais armazenados pelo app.

A consulta por código de barras é uma exceção: quando usada, o código informado ou lido pela câmera é enviado diretamente ao Open Food Facts para localizar o produto e seus dados nutricionais. A base do Open Food Facts é alimentada por contribuições e os dados podem estar incompletos ou incorretos; confira o rótulo do produto.

## GitHub Pages

Como é uma aplicação estática, basta publicar `index.html` pela branch principal e pela pasta raiz usando GitHub Pages.
