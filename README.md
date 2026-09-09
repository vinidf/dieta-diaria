# Dieta Diária

App web estático em português do Brasil para acompanhar uma dieta diária sem backend.

## Recursos

- 5 refeições fixas: 06h, 09h, 12h, 16h e 20h.
- Checkbox por item.
- Totais automáticos de calorias, carboidratos, proteínas, fibras e gorduras dos itens consumidos.
- Indicadores visuais no topo.
- Adição rápida de itens para o dia atual.
- Edição e exclusão de itens do dia atual.
- Versionamento de cada dia no `localStorage`.
- Histórico de versões diárias.
- Exportação/importação de backup JSON.
- Importação e cadastro/edição da dieta-base em JSON.
- Sem backend e sem envio de dados para terceiros.

## Formato JSON da dieta

```json
{
  "schemaVersion": 1,
  "name": "Minha dieta",
  "meals": [
    {
      "id": "cafe",
      "name": "Café da manhã",
      "time": "06:00",
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
      "id": "lanche",
      "name": "Lanche",
      "time": "09:00",
      "items": []
    },
    {
      "id": "almoco",
      "name": "Almoço",
      "time": "12:00",
      "items": []
    },
    {
      "id": "tarde",
      "name": "Lanche da tarde",
      "time": "16:00",
      "items": []
    },
    {
      "id": "jantar",
      "name": "Jantar",
      "time": "20:00",
      "items": []
    }
  ]
}
```

Os valores nutricionais são referentes à porção representada pelo item.

## Armazenamento

A chave `dietaDiaria.v1` do `localStorage` guarda a dieta-base e o histórico por data. Cada alteração gera uma nova versão do dia, permitindo recuperar o estado anterior através do backup/histórico.

Exemplo conceitual:

```json
{
  "schemaVersion": 1,
  "diet": { "...": "dieta-base" },
  "days": {
    "2026-09-09": [
      {
        "date": "2026-09-09",
        "version": 1,
        "savedAt": "2026-09-09T12:00:00.000Z",
        "meals": []
      },
      {
        "date": "2026-09-09",
        "version": 2,
        "savedAt": "2026-09-09T13:00:00.000Z",
        "meals": []
      }
    ]
  }
}
```

## Privacidade

O aplicativo é estático e não possui conta, servidor próprio, banco de dados, analytics ou chamadas para APIs externas. Os dados inseridos pelo usuário ficam no `localStorage` do navegador e só saem do dispositivo quando o próprio usuário exporta um backup JSON.

O repositório não contém dados pessoais, credenciais, tokens, chaves de API ou arquivos de configuração secretos.

## Direitos e dependências

O código deste projeto foi produzido para este projeto e a versão publicada não inclui bibliotecas externas, imagens de terceiros, fontes externas, ícones externos ou trechos identificados de código de terceiros. O exemplo nutricional de ovo no editor é apenas um dado demonstrativo de teste e não constitui uma base nutricional completa.

Antes de reutilizar código, textos, dados nutricionais ou outros materiais de terceiros em futuras versões, verifique a licença e os respectivos direitos de uso.
