# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Interações Anteriores para Aprender sobre Comportamento e Padrões |
| `investidorprofile.json` | JSON | Utilizar como "Few Shot" para estudar o Comportamento de um Perfil de Investidor|
| `produtos_financeiros.json` | JSON | Investimentos de Renda Simples Disponível no Mercado |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |
| `perfil_investidor.json` | JSON | Explicar cada tipo de perfil de investidor com um FewShot para cada um |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Alterei e expandi os dados. O "perfil_investidor" virou "investidorprofile" e virou exemplo de fewshot para a IA se basear na prática um perfil de investidor. No "perfíl_investidor" atual, agora possui todos os populares tipos de perfil de investidor com exemplos práticos de cada um, para que possa estudar comportamentos e padrões. E o "produtos_financeiros" modifiquei colocando a adaptabilidade do mercado e os investimentos de mais alta recorrência de visualização nos diferentes perfis. 

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.
Como necessita de uma base de dados já consolidada, poderiamos ou colocar no prompt (CTRL+C CTRL+V) ou implementar via código, ex:
```python
import pandas as pd
import json

transacoes = pd.read_csv("data/transacoes.csv")
historico = pd.read_csv("data/historico_atendimento.csv")

with open ("data/investidorprofile.json","r", encodings="utf-8") as f:
    investidor = json.load(f)

with open ("data/perfil_investidor.json","r", encodings="utf-8") as f:
    perfilInv = json.load(f)

with open ("data/produtos_financeiros.json","r", encodings="utf-8") as f:
    produtos = json.load(f)
```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Os dados coletados serão relativos as informações fornecidas e a prioridade de otimizar tokens - desde que não prejudique a coleta das informações cruciais, se possivel, devem seguir uma base semelhante a base de conhecimento fornecida. Abaixo, um exemplo de quais variáveis podem ser armazenadas e como serao:

```text
USUÁRIO E SEU PERFIL (data/perfil_investidor.json):
{
  "nome": "João Silva",
  "idade": 32,
  "profissao": "Analista de Sistemas",
  "renda_mensal": 5000.00,
  "perfil_investidor": "moderado",}

FATOR ECONÔMICO E METAS:
  {
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 15000.00,
  "reserva_emergencia_atual": 10000.00,
  "aceita_risco": false,
  "metas": [
    {
      "meta": "Completar reserva de emergência",
      "valor_necessario": 15000.00,
      "prazo": "2026-06"
    },
    {
      "meta": "Entrada do apartamento",
      "valor_necessario": 50000.00,
      "prazo": "2027-12"
    }
  ]
}

POSSÍVEIS INVESTIMENTOS E AÇÕES FUTURAS (data/produtos_financeiros.json):
{
  "perfil": "moderado",
  "momento": "formacao_de_reserva",
  "melhor_escolha_atual": [
    "Tesouro Selic",
    "CDB Liquidez Diária"
  ],
  "evitar_por_enquanto": [
    "Ações",
    "Fundos de ações",
    "ETFs de bolsa"
  ],
  "proxima_etapa": "Concluir reserva de R$ 15.000",
  "apos_reserva": "Começar acumulação para entrada do apartamento com Tesouro IPCA+, CDBs e pequena diversificação"
}

ULTIMAS TRANSAÇÕES(data/transacoes.csv):
data,descricao,categoria,valor,tipo
2025-10-01,Salário,receita,5000.00,entrada
2025-10-02,Aluguel,moradia,1200.00,saida
2025-10-03,Supermercado,alimentacao,450.00,saida
2025-10-05,Netflix,lazer,55.90,saida
2025-10-07,Farmácia,saude,89.00,saida
2025-10-10,Restaurante,alimentacao,120.00,saida
2025-10-12,Uber,transporte,45.00,saida
2025-10-15,Conta de Luz,moradia,180.00,saida
2025-10-20,Academia,saude,99.00,saida
2025-10-25,Combustível,transporte,250.00,saida

```

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Usuário:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000
- Saldo investido: R$ 3.000
- Renda parada: R$ 2.000
- Investimentos: CDB, Tesouro Selic

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
