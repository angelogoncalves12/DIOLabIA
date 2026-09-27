# Código da Aplicação

Esta pasta contém o código do seu agente financeiro.

## Estrutura Utilizada

```
src/
├── app.py              # Aplicação principal (customtkinter)
├── .env                # Configurações (API keys, etc.)
└── requirements.txt    # Dependências
```

## Exemplo de requirements.txt

```
streamlit
openai
python-dotenv
```

## Como Rodar

```bash
# Instalar dependências
pip install -r requirements.txt

# Rodar a aplicação
streamlit run app.py
```
