# 💬 Aplicativo Cliente-Servidor de Mensagens com Autenticação

Aplicação **cliente-servidor** que simula um sistema de **troca de mensagens em tempo real** entre usuários autenticados.  
O sistema foi desenvolvido em grupo, com **interface gráfica em Tkinter** para o cliente e **servidor TCP multithread** em Python.

🔐 Inclui **login com autenticação**, **mensagens públicas e privadas**, **envio de arquivos** e **registro de logs**.

---

## 🧩 Sumário
- [Descrição Geral](#descrição-geral)
- [Arquitetura](#arquitetura)
- [Funcionalidades](#funcionalidades)
- [Requisitos](#requisitos)
- [Como Executar](#como-executar)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Tecnologias](#tecnologias)
- [Colaboradores](#colaboradores)
- [Licença](#licença)

---

## 🧠 Descrição Geral

O projeto implementa um sistema de **chat local** baseado no modelo **Cliente-Servidor**, com comunicação via **sockets TCP**.  
Cada cliente realiza login com **usuário e senha**, e pode trocar mensagens com todos os usuários conectados ou enviar mensagens privadas com o prefixo `@username`.

Além disso, o cliente pode **enviar arquivos** para o servidor e acompanhar **quem está online em tempo real**.

---

## ⚙️ Arquitetura

```text
┌──────────────────────┐
│      Servidor        │
│  • Gera logs          │
│  • Gerencia logins    │
│  • Difunde mensagens  │
│  • Controla usuários  │
└────────┬─────────────┘
         │ TCP Socket
┌────────┴─────────────┐
│       Cliente         │
│  • Login GUI (Tkinter)│
│  • Envio de mensagens  │
│  • Envio de arquivos   │
│  • Lista de usuários   │
└───────────────────────┘
````

Cada cliente se conecta ao servidor via `socket` e interage de forma assíncrona usando **threads** para envio e recebimento de dados.

---

## 💡 Funcionalidades

### 🔐 Autenticação

* Login com **usuário e senha** definidos no servidor.
* Validação de credenciais antes da entrada no chat.

### 💬 Mensagens

* Envio de mensagens públicas para todos os usuários.
* Mensagens privadas via `@username <mensagem>`.
* Exibição local formatada: `"Você: mensagem"`.

### 📁 Envio de Arquivos

* Envio de arquivos de texto do cliente para o servidor.
* Armazenamento automático no servidor como `outputX.txt`.

### 👥 Lista de Usuários Online

* Atualizada em tempo real com todos os clientes conectados.

### 🧾 Log do Servidor

* Cada sessão gera logs automáticos em `/logs/` com:

  * Mensagens trocadas
  * Conexões e desconexões
  * Tentativas de login inválidas

---

## 📦 Requisitos

* **Python 3.8+**
* Bibliotecas padrão: `socket`, `threading`, `tkinter`, `logging`, `os`, `datetime`

Nenhuma instalação extra é necessária.

---

## 🧭 Como Executar

1️⃣ **Inicie o servidor:**

```bash
python server.py
```

2️⃣ **Em outro terminal (ou máquina local), execute o cliente:**

```bash
python client.py
```

3️⃣ **Login:**
Use uma das credenciais cadastradas no servidor:

| Usuário | Senha  |
| ------- | ------ |
| admin   | admin  |
| dely    | 1234   |
| arthur  | 4321   |
| gabriel | senha  |
| victor  | 123456 |
| juan    | 123    |

---

## 🧱 Estrutura do Projeto

```text
├── client.py        # Interface gráfica e comunicação com o servidor
├── server.py        # Gerencia conexões, autenticação e troca de mensagens
├── logs/            # Diretório onde os logs diários são armazenados
└── README.md
```

---

## 🖼️ Interface do Cliente

* Desenvolvida com **Tkinter**
* Tema escuro moderno (`bg="#1c1c1c"`)
* Componentes:

  * Tela de **login**
  * Tela de **chat com lista de usuários**
  * Campos para **mensagens** e **envio de arquivos**

---

## 🧰 Tecnologias Utilizadas

| Categoria           | Ferramenta / Biblioteca |
| ------------------- | ----------------------- |
| Linguagem           | Python 3                |
| Interface Gráfica   | Tkinter                 |
| Comunicação         | Socket TCP              |
| Concorrência        | Threading               |
| Logging             | Módulo `logging`        |
| Sistema de Arquivos | `os`, `datetime`        |

---

## 👥 Colaboradores

Desenvolvido em grupo por:

* [**Dely Silva**](https://github.com/delysilva)
* [**Gabriel**](https://github.com/gabsizinio)
* [**Arthur Silva**](https://github.com/arthursilva35)
* [**Victor Sales**](https://github.com/victorsales1709)

---

## 📄 Licença

Este projeto é distribuído sob a licença **MIT**.
Consulte o arquivo `LICENSE` para mais informações.

---

> 💬 Projeto educacional para estudo de **redes, autenticação e programação concorrente em Python**, demonstrando um modelo prático de **comunicação cliente-servidor com interface gráfica.**

