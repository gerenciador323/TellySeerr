# [TellySeerr]
[![Python Version](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/downloads/)
[![Linter: Ruff](https://img.shields.io/badge/linter-ruff-brightgreen.svg)](https://github.com/astral-sh/ruff)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Um bot poderoso e tudo‑em‑um para o Telegram para gerenciar seus servidores Jellyfin e Jellyseerr. Ele atua como um gateway completo tanto para você quanto para seus usuários, automatizando convites, lidando com pedidos de mídia e fornecendo estatísticas de reprodução.

## ✨ Funcionalidades principais

### 👑 Gerenciamento de administradores
* **Convites de usuários de forma simples:** Basta responder a um usuário no Telegram para convidá‑lo:
    * `/invite`: Cria uma conta completa e permanente no Jellyfin/Jellyseerr.
    * `/trial`: Cria uma conta de teste de 7 dias.
    * `/vip`: Cria uma conta VIP de 30 dias.
* **Gerenciamento de usuários:**
    * `/deleteuser <username>`: Exclui um usuário do Jellyfin, Jellyseerr e do banco de dados do bot.
    * `/listusers`: Mostra uma lista completa de todos os usuários no seu servidor Jellyfin.
* **Limpeza automática:** Uma tarefa em background é executada diariamente para encontrar e excluir automaticamente usuários de teste/VIP expirados de todos os serviços.

### 👤 Funcionalidades para usuários
* **Vinculação self‑service:** Usuários com contas existentes podem vinculá‑las ao bot com `/link <username> <password>`.
* **Estatísticas pessoais:** Usuários podem executar `/watch` para ver seu tempo total assistido e o total de itens reproduzidos a partir do Jellyfin.

### 🎬 Pedidos de mídia (via Jellyseerr)
* **Busca e descoberta:**
    * `/request <name>`: Busca por novos filmes e séries.
    * `/discover`: Mostra uma lista navegável de mídias populares e em alta.
* **Sistema completo de pedidos:**
    * Usuários podem enviar pedidos de mídia diretamente por meio de botões interativos.
    * `/requests`: Usuários podem ver o status de todos os seus pedidos pendentes.
* **Cache inteligente:** Resultados de busca e descoberta são armazenados em cache por 1 hora para reduzir spam na API e melhorar a velocidade.

---

## 🚀 Primeiros passos

### Pré‑requisitos

1.  Um **bot do Telegram**. Obtenha seu `BOT_TOKEN` com o [BotFather](https://t.me/botfather).
2.  Seu **Telegram API ID e Hash**. Obtenha em [my.telegram.org](https://my.telegram.org).
3.  Um servidor **Jellyfin**. Você precisa da **URL do servidor** e de uma **API Key** (gere uma em Dashboard > API Keys).
4.  Um servidor **Jellyseerr**. Você precisa da **URL do servidor** e da sua **API Key** (encontre em Jellyseerr Settings > General).
5.  **Python 3.11+**
6.  **Pipenv** (para gerenciar dependências).

### ⚙️ Instalação e configuração

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/DESTROYER-32/TellySeerr.git](https://github.com/DESTROYER-32/TellySeerr.git)
    cd your-repo-name
    ```

2.  **Instale as dependências usando o Pipenv:**
    ```bash
    pipenv install
    ```
    Isto criará um ambiente virtual e instalará todos os pacotes a partir do `Pipfile.lock`.

3.  **Configure seu bot:**
    Copie o arquivo de ambiente de exemplo para criar seu próprio arquivo de segredos.
    ```bash
    cp .env.sample .env
    ```
    Agora, edite o arquivo `.env` com suas chaves de API e URLs. É fundamental que você **não** use aspas (`"`) ao redor dos valores.

    ```ini
    # --- .env file ---
    TELEGRAM_API_ID=1234567
    TELEGRAM_API_HASH=your_api_hash_here
    TELEGRAM_BOT_TOKEN=your_bot_token_here

    JELLYSEERR_URL=[https://jellyseerr.example.com](https://jellyseerr.example.com)
    JELLYSEERR_API_KEY=your_jellyseerr_api_key_here

    JELLYFIN_URL=[https://jellyfin.example.com](https://jellyfin.example.com)
    JELLYFIN_API_KEY=your_jellyfin_api_key_here

    # Your personal Telegram User ID
    ADMIN_USER_IDS=[123456789, 987654321]
    ```

4.  **Execute o bot:**
    ```bash
    pipenv run python main.py
    ```
    O bot será iniciado, conectará ao Telegram, definirá seus comandos e inicializará o banco de dados.

---

## 🤖 Comandos do bot

O bot definirá automaticamente esses comandos no menu do Telegram para você. Administradores verão uma lista estendida.

### Comandos de usuário
| Comando | Descrição |
| --- | --- |
| `/start` | Inicia o bot |
| `/help` | Mostra a mensagem de ajuda |
| `/request` | Solicita um filme/série. Uso: `/request <name>` |
| `/discover` | Descobre mídias populares e em alta |
| `/requests` | Exibe seus pedidos de mídia pendentes |
| `/watch` | Mostra suas estatísticas pessoais de reprodução |
| `/link` | Vincula sua conta Jellyfin. Uso: `/link <user> <pass>` |
| `/unlink` | Desvincula sua conta Jellyfin |

### Comandos apenas para admins
| Comando | Descrição |
| --- | --- |
| `/invite` | Responda a um usuário para criar uma conta permanente |
| `/trial` | Responda a um usuário para criar uma conta de teste de 7 dias |
| `/vip` | Responda a um usuário para criar uma conta VIP de 30 dias |
| `/deleteuser` | Exclui um usuário. Uso: `/deleteuser <username>` |
| `/listusers` | Lista todos os usuários no servidor Jellyfin |

---

## 🤝 Contribuindo

Contribuições são bem‑vindas! Se você quiser corrigir um bug ou adicionar uma nova funcionalidade, leia o arquivo `CONTRIBUTING.md` para obter detalhes sobre como:

* Reportar bugs e sugerir funcionalidades
* Configurar seu ambiente de desenvolvimento
* Seguir o estilo de código e enviar suas alterações

---

## 📜 Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.