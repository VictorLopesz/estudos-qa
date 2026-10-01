# 01 · SQL (MySQL)

## Objetivo
Consultar e validar dados como QA: SELECT, JOIN, GROUP BY, subqueries, CTE, transações, massa de dados e validação no banco depois de testes de API e de tela.

## 🛠️ Ambiente
MySQL Community Server 8.4 LTS instalado direto no Mac (sem Docker) + DBeaver. Banco `loja_qa`, usuário próprio (não usar o root nos testes).

## 📂 Estrutura
- `schema.sql` / `seeds.sql` — tabelas e massa de dados
- `exercicios/` — consultas numeradas (`01-select.sql`, `02-joins.sql`, ...)
- `scripts/` — geração de massa com Faker + mysql2 (`gerar-massa.ts`)
- `api-loja/` — mini API (Node + Express + mysql2) usada depois no Postman, no Cypress e no CI

## ▶️ Como instalar e conectar

### 1. Instalar o MySQL (macOS Apple Silicon, sem Docker)
1. Baixar em [dev.mysql.com/downloads/mysql](https://dev.mysql.com/downloads/mysql/): versão **8.4.x LTS**, **macOS (ARM, 64-bit), DMG Archive** ("No thanks, just start my download").
2. Rodar o instalador e escolher **Use Strong Password Encryption**. Definir a senha do `root` (guardar num gerenciador de senhas).
3. Conferir em **Ajustes do Sistema → MySQL**: o servidor deve estar rodando (bolinha verde). É ali que se para e inicia o MySQL.

### 2. Colocar o `mysql` no terminal
```bash
echo 'export PATH="/usr/local/mysql/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
mysql --version
```

### 3. Criar o banco e o usuário de testes
```bash
mysql -u root -p
```
```sql
CREATE DATABASE loja_qa;
CREATE USER 'qa'@'localhost' IDENTIFIED BY '<senha do qa>';
GRANT ALL PRIVILEGES ON loja_qa.* TO 'qa'@'localhost';
SHOW GRANTS FOR 'qa'@'localhost';
EXIT;
```
- O `qa` só acessa o `loja_qa` (menor privilégio). O `root` fica só para administrar.
- Testar: `mysql -u qa -p loja_qa`

### 4. Conectar no DBeaver
1. **Nova conexão → MySQL**.
2. Host `localhost` · Porta `3306` · Database `loja_qa` · Username **`qa`** · Password: a senha do `qa`.
3. Aba **Driver properties**: `allowPublicKeyRetrieval = true` e `useSSL = false` (só para o banco local).
4. **Test Connection → Finish**.

### 5. Variáveis de ambiente
Copiar o [`.env.example`](../.env.example) para `.env` na raiz do repositório e preencher a senha do `qa`. O `.env` está no `.gitignore` e nunca vai para o GitHub.

### 🧯 Erros que encontrei
| Erro | Causa | Solução |
|---|---|---|
| `ERROR 1410: You are not allowed to create a user with GRANT` | O usuário do `GRANT` não existe (digitei `localholst` em vez de `localhost`) | Corrigir o nome/host. No MySQL 8 o `GRANT` não cria usuário |
| `Public Key Retrieval is not allowed` (DBeaver) | MySQL 8 sem SSL precisa buscar a chave pública do servidor | `allowPublicKeyRetrieval = true` nas Driver properties |
| `Access denied for user 'root'@'localhost'` (DBeaver) | A conexão veio com `root` por padrão e usei a senha do `qa` | Trocar o Username para `qa` |
| Mudar a senha do `qa` | — | Como root: `ALTER USER 'qa'@'localhost' IDENTIFIED BY '<nova senha>';` |

## ✅ O que aprendi
-
