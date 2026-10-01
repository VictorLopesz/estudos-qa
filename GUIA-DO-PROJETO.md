# 🧭 Guia do projeto — o que fazer em cada pasta e arquivo

A regra principal: **quase tudo aqui só é usado mais para frente.** Cada pasta entra em cena no dia em que o cronograma (planilha) chega naquele tema.

---

## 🗂️ O que você usa desde o primeiro dia

| Item | O que é | O que fazer |
|---|---|---|
| **`README.md`** (raiz) | A "vitrine" do portfólio: é a primeira coisa que quem abrir o seu GitHub vê. Tem a tabela dos módulos. | Atualize o status de cada módulo conforme avança (⏳ Não iniciado → ✅ Concluído). |
| **`diario/`** | O seu caderno de anotações, com uma pasta por tema. | Toda manhã, crie o arquivo do dia na pasta do tema e anote enquanto estuda. |
| **`diario/_modelo.md`** | O molde da anotação (o que estudei, o que pratiquei, recursos, dúvidas). | **Não edite.** Copie, cole na pasta do tema e renomeie. |
| **`diario/README.md`** | Explica as pastas e o padrão de nome (`SQL-02-10-2026.md`...). | Só consulta. |

---

## 📚 As pastas dos temas

Cada pasta tem um **`README.md`**, que é o guia do tema: objetivo, o que vai ter ali e o espaço "O que aprendi". **Preencha aos poucos.** As subpastas começam vazias e recebem os arquivos que você cria na prática.

### `00-mcp/` — MCP + IA para QA
O README traz a cola de comandos do `claude mcp` e as regras de segurança. As aulas criam aqui as explorações com Playwright MCP, os casos gerados pela IA (com a sua revisão), o checklist de segurança e o seu servidor MCP (`servidor-massa/`).

### `01-sql/` — SQL (MySQL)
- O MySQL fica instalado direto no Mac (sem Docker) e você acessa pelo DBeaver.
- `schema.sql` (as tabelas) e `seeds.sql` (os dados) ficam na raiz da pasta.
- `exercicios/` → as suas consultas SQL numeradas, uma por aula (`01-select.sql`, `02-joins.sql`...).
- `scripts/` → o script que gera dados de teste com Faker + mysql2 (mais para frente).
- `api-loja/` → a mini API (Express + MySQL) que depois é testada no Postman, no Cypress e no CI.

### `02-api-rest/` — Testes de API REST
- `postman/` → a collection do Postman exportada (arquivo `.json`).
- `postman/dados/` → planilhas CSV para rodar testes com vários dados.
- `schemas/` → os "contratos" da API (JSON Schema), usados no Postman e no Cypress.
- `cypress-api/` → testes de API escritos com Cypress (`cy.request`), em uma aula mais para frente.

### `03-cypress/` — Cypress avançado (TypeScript)
Na primeira aula de Cypress você cria aqui o projeto, testando o site **front.serverest.dev**. O README já traz a estrutura que o projeto vai ter:
- `e2e/` → os testes
- `pages/` → os Page Objects
- `support/` → os custom commands
- `fixtures/` → os dados

### `04-ci-cd/` — CI/CD
- `jenkins/` → um Jenkinsfile de exemplo (aula de Jenkins).
- Os pipelines de verdade **não ficam aqui**, e sim em `.github/workflows/` (veja abaixo). Esta pasta guarda anotações e o Jenkinsfile.

---

## ⚙️ Arquivos "escondidos" (começam com ponto)

No VS Code eles aparecem normalmente. No Finder, ficam ocultos.

| Arquivo | O que é | O que fazer |
|---|---|---|
| **`.gitignore`** | A lista do que o Git **deve ignorar**: senhas, `.env`, `node_modules`, vídeos e relatórios de teste. Protege você de publicar segredos. | Nada. Já está pronto. |
| **`.env.example`** | Exemplo das configurações do MySQL (host, usuário, senha, banco). | Na aula de SQL, copie para um arquivo `.env` e coloque a sua senha. O `.env` **nunca** sobe para o GitHub; o `.example` sobe, sem senha. |
| **`.github/workflows/`** | Onde ficam os pipelines do GitHub Actions. **O GitHub exige que fiquem aqui, na raiz.** | Fica vazio até as aulas de CI/CD. |
| **`.github/pull_request_template.md`** | O texto que aparece sozinho quando você abre um Pull Request, com um checklist ("nenhum segredo commitado" etc.). | Nada. O GitHub usa automaticamente. |

---

## 🧩 E os arquivos `.gitkeep`?

O Git **não salva pastas vazias**. O `.gitkeep` é um arquivo vazio que serve só para a pasta aparecer no GitHub. **Ignore-os.** Quando você colocar um arquivo de verdade na pasta, pode apagar o `.gitkeep` dela, se quiser.

---

## ✅ Rotina de um dia de estudo

1. **Manhã (09:30–11:00):** abra a planilha e veja o tema e os recursos do dia.
2. Crie o arquivo do dia em `diario/<tema>/` a partir do `_modelo.md` (ex.: `diario/sql/SQL-02-10-2026.md`) e anote enquanto estuda.
3. Faça a prática na pasta do tema (ex.: `01-sql/exercicios/02-joins.sql`).
4. O que ficar claro de vez vai para o `README.md` do tema (a sua cola consolidada).
5. Salve no GitHub:
   ```bash
   git add .
   git commit -m "feat(sql): exercícios de JOIN"
   git push
   ```
6. **Noite (21:00–22:00):** releia a anotação e reveja os vídeos da manhã do dia de estudo anterior. Não precisa criar arquivo.

### Mudança de plano (01/10)
O plano foi refeito: saíram Git/GitHub/GitLab e Docker; entraram MySQL e MCP. O que foi feito no dia 01/10 (Git) ficou como histórico em `diario/git/`.

### Primeira aula de SQL (02/10)
1. Instalar o MySQL 8.4 LTS no Mac, criar o banco `loja_qa` e um usuário próprio.
2. Conectar pelo DBeaver.
3. Copiar `.env.example` para `.env` e preencher a sua senha.
4. Criar `diario/sql/SQL-02-10-2026.md` e anotar; registrar o passo a passo no `01-sql/README.md`.
