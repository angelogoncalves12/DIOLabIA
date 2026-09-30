# 🤖 Thomas - Assistente Financeiro IA

O **Thomas** é uma aplicação desktop desenvolvida em Python com interface gráfica intuitiva em CustomTkinter e integração com o modelo de inteligência artificial da Groq (compatível com a API OpenAI). O objetivo do Thomas é atuar como um conselheiro financeiro pessoal descontraído, auxiliando o usuário na organização de investimentos, quitação de dívidas e análise de transações financeiras locais.

---

## 🛠️ Tecnologias Utilizadas

* **Python 3.10+** — Linguagem principal do projeto.
* **CustomTkinter** — Interface gráfica desktop moderna com suporte a modo escuro e controle de zoom.
* **Pandas** — Leitura e manipulação da base de dados financeira em CSV.
* **python-dotenv** — Gerenciamento seguro das variáveis de ambiente.
* **OpenAI SDK** — Cliente de comunicação direcionado à API compatível da **Groq**.

---

## 📂 Estrutura do Projeto

```text
DADOS DA IA FINANCEIRA/
├── .env                     # Variáveis de ambiente (Chave de API)
├── requirements.txt         # Dependências do projeto
├── aplication.py            # Código-fonte principal da aplicação
├── README.md                # Documentação de instalação e uso
└── data/                    # Base de dados local da IA
    ├── investidorprofile.json
    ├── perfil_investidor.json
    ├── produtos_financeiros.json
    ├── transacoes.csv
    └── historico_atendimento.csv
```

🚀 Como Rodar o Projeto

Siga os passos abaixo para configurar o ambiente e executar o Thomas na sua máquina:
1. Pré-requisitos

    Ter o Python 3.10 ou superior instalado (Download Python).

    Obter uma chave de API gratuita na Groq Cloud Console.

2. Passo a Passo de Instalação
Passo 1: Clonar o Repositório
Bash

git clone [https://github.com/seu-usuario/thomas-ia.git](https://github.com/angelogoncalves12/DIOLabIA cd 
Passo 2: Criar e Ativar um Ambiente Virtual (Opcional, mas recomendado)

    No Linux / macOS:
    Bash

    python3 -m venv venv
    source venv/bin/activate

    No Windows (PowerShell):
    PowerShell

    python -m venv venv
    .\venv\Scripts\Activate.ps1

Passo 3: Instalar as Dependências
Bash

pip install -r requirements.txt

3. Configuração do Arquivo .env

Na raiz do projeto, crie um arquivo chamado .env (ou edite o existente) e adicione a sua chave da Groq:
Snippet de código

GROQ_API_KEY=sua_chave_groq_aqui
GROQ_MODEL=openai/gpt-oss-120b

    ⚠️ Atenção: O programa não iniciará caso a variável GROQ_API_KEY não esteja presente no .env.

4. Executar a Aplicação

Com o ambiente configurado, execute o arquivo principal:
Bash

python aplication.py

🖥️ Funcionalidades da Interface

    Chat Assíncrono (Threading): A interface não trava enquanto o Thomas está processando e gerando a resposta.

    Controle de Zoom (A+ / A-): Botões laterais no menu para ajustar dinamicamente o tamanho da fonte do chat conforme a necessidade.

    Leitura da Base Local: Botões no menu para visualizar instantaneamente o perfil carregado (Ver Perfil) e o histórico tabular (Transações).

    Formatador de Respostas: Remoção automática de Markdown complexo para garantir legibilidade perfeita no CustomTkinter.

🛡️ Segurança e Privacidade

    O Thomas nunca salva ou solicita dados sensíveis como senhas, números completos de cartão ou chaves PIX bancárias.

    A chave de API permanece local e protegida pelo arquivo .env (certifique-se de que o .env esteja listado no seu .gitignore).
