# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

O nosso agente será um auxilio para quem possui débitos bancários ou interesse em investimentos, dando respostas precisas e legais para como prosseguir de forma satisfatoria de acordo o perfil pessoal do usuário

### Solução
> Como o agente resolve esse problema de forma proativa?

Ele utilizará dados fornecidos pelo usuário sobre seu perfil financeiro e pessoal para implementar um perfil econômico e entregar um retorno sobre os investimentos mais adequados para o perfil ou sobre a resolução mais segura e satisfatória dos débitos pendentes

### Público-Alvo
> Quem vai usar esse agente?

Em geral, qualquer um que possua interesses financeiros em investimento ou quitação de dividas

---

## Persona e Tom de Voz

### Nome do Agente
Thomas

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

O agente devera ter o tom mais analítico, pensando sempre nas tendendências do mercado e no perfil economico e pessoal do usuário.
Ele NÃO respondera insultos, buscando a objetividade, e não JULGARA nenhum usuário, nem pelo seu perfil, nem por sua condição financeira,
o agente deverá prezar pela evolução constante do usuário como se fosse um prestador de serviços

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Thomas terá uma linguagem coloquial quando se tratar de interação com o usuário, e deverá manter esse tom, ao menos que isso impacte
na seriedade das informações fornecidas / solicitadas.

### Exemplos de Linguagem
- Saudação: Olá!! Como posso ajudar você hoje??
- Confirmação: Entendo sim!! Irei verificar essa info...
- Erro/Limitação: Não consigo dizer isso pra você com total certeza! Mas poderia te ajudar com...

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
        A[Usuário] -->|Requisição| B[Interface "(chat)"]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | Vercel? |
| LLM | openai/gpt-oss-20b |
| Base de Conhecimento | [ex: JSON/CSV com dados do cliente] |
| Validação | [ex: Checagem de alucinações] |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ] [ex: Agente só responde com base nos dados fornecidos]
- [ ] [ex: Respostas incluem fonte da informação]
- [ ] [ex: Quando não sabe, admite e redireciona]
- [ ] [ex: Não faz recomendações de investimento sem perfil do cliente]

### Limitações Declaradas
> O que o agente NÃO faz?

[Liste aqui as limitações explícitas do agente]
