# Dieta Diária

App web estático em português do Brasil para acompanhar uma dieta diária sem backend.

## Recursos

- Quantidade configurável de 1 a 12 refeições por dia.
- Nome e horário configuráveis para cada refeição.
- Itens nutricionais configuráveis por refeição.
- Checkbox por item.
- Totais automáticos de calorias, carboidratos, proteínas, fibras e gorduras dos itens consumidos.
- Indicadores visuais no topo.
- Adição rápida de itens para o dia atual.
- Edição e exclusão de itens do dia atual.
- Versionamento de cada dia no `localStorage`.
- Histórico de versões diárias.
- Exportação/importação de backup JSON.
- Importação e cadastro/edição da dieta-base em JSON.
- Migração automática da versão anterior com 5 refeições fixas.
- Sem backend e sem envio de dados para terceiros.

## Configuração das refeições

Na opção **Configurar dieta e refeições**, a pessoa escolhe de 1 a 12 refeições por dia e define o nome e o horário de cada uma. Ao salvar, os novos dias passam a usar essa estrutura. Itens das refeições existentes são preservados quando possível.

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

Os valores nutricionais são referentes à porção representada pelo item.

## Armazenamento

A chave `dietaDiaria.v2` do `localStorage` guarda a dieta-base e o histórico por data. Cada alteração gera uma nova versão do dia. A versão anterior `dietaDiaria.v1` é migrada automaticamente quando encontrada.

## Privacidade e direitos

Não há conta, backend, analytics, API externa, imagens externas, fontes externas ou bibliotecas de terceiros. Os dados registrados pelo usuário ficam somente no navegador. O backup exportado contém apenas a estrutura da dieta e os registros locais armazenados pelo app.

O repositório contém somente o código e a documentação do aplicativo, sem dados pessoais do usuário.

## GitHub Pages

Como é uma aplicação estática, basta publicar `index.html` pela branch principal e pela pasta raiz usando GitHub Pages.
