# 🧭 Guia do projeto — o que fazer em cada pasta e arquivo

A regra principal: **quase tudo aqui só é usado mais para frente.** Cada pasta entra em cena no dia em que o cronograma (planilha) chega naquele tema.

---

## 🗂️ O que você usa desde o primeiro dia

| Item | O que é | O que fazer |
|---|---|---|
| **`README.md`** (raiz) | A "vitrine" do portfólio: é a primeira coisa que quem abrir o seu GitHub vê. Tem a tabela dos módulos. | Atualize o status de cada módulo conforme avança (⏳ Não iniciado → ✅ Concluído). |
| **`diario/`** | O seu caderno de anotações, com uma pasta por tema. | Toda manhã, crie o arquivo do dia na pasta do tema e anote enquanto estuda. |
| **`diario/_modelo.md`** | O molde da anotação (o que estudei, o que pratiquei, recursos, dúvidas). | **Não edite.** Copie, cole na pasta do tema e renomeie. |
| **`diario/README.md`** | Explica as pastas e o padrão de nome (`GIT-01-10-2026.md`...). | Só consulta. |
| **`00-git/README.md`** | A sua "cola" de Git, com uma tabela de comandos para preencher. | Quando entender um comando de vez, anote aqui o que ele faz. |

---

## 📚 As pastas dos temas

Cada pasta tem um **`README.md`**, que é o guia do tema: objetivo, o que vai ter ali e o espaço "O que aprendi". **Preencha aos poucos.** As subpastas começam vazias e recebem os arquivos que você cria na prática.

### `00-git/` — Git, GitHub e GitLab
Só o README com a sua cola de comandos. A prática de Git acontece no próprio repositório: commits, branches e Pull Requests.

### `01-sql/` — SQL (PostgreSQL) + Docker
- `exercicios/` → as suas consultas SQL numeradas, uma por aula (`01-select.sql`, `02-joins.sql`...).
- `scripts/` → o script que gera dados de teste com Faker (mais para frente).
- Na primeira aula de SQL você cria aqui o `docker-compose.yml`, que sobe o banco PostgreSQL, e depois o `schema.sql` (as tabelas) e o `seeds.sql` (os dados).

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
- Os pipelines de verdade **não ficam aqui**, e sim em `.github/workflows/` (veja abaixo). Esta pasta guarda anotações e os arquivos do GitLab e do Jenkins.

---

## ⚙️ Arquivos "escondidos" (começam com ponto)

No VS Code eles aparecem normalmente. No Finder, ficam ocultos.

| Arquivo | O que é | O que fazer |
|---|---|---|
| **`.gitignore`** | A lista do que o Git **deve ignorar**: senhas, `.env`, `node_modules`, vídeos e relatórios de teste. Protege você de publicar segredos. | Nada. Já está pronto. |
| **`.env.example`** | Exemplo das configurações do banco (usuário, senha). | Na aula de SQL, copie para um arquivo `.env` e coloque a sua senha. O `.env` **nunca** sobe para o GitHub; o `.example` sobe, sem senha. |
| **`.github/workflows/`** | Onde ficam os pipelines do GitHub Actions. **O GitHub exige que fiquem aqui, na raiz.** | Fica vazio até as aulas de CI/CD. |
| **`.github/pull_request_template.md`** | O texto que aparece sozinho quando você abre um Pull Request, com um checklist ("nenhum segredo commitado" etc.). | Nada. O GitHub usa automaticamente. |

---

## 🧩 E os arquivos `.gitkeep`?

O Git **não salva pastas vazias**. O `.gitkeep` é um arquivo vazio que serve só para a pasta aparecer no GitHub. **Ignore-os.** Quando você colocar um arquivo de verdade na pasta, pode apagar o `.gitkeep` dela, se quiser.

---

## ✅ Rotina de um dia de estudo

1. **Manhã (09:30–11:00):** abra a planilha e veja o tema e os recursos do dia.
2. Crie o arquivo do dia em `diario/<tema>/` a partir do `_modelo.md` (ex.: `diario/git/GIT-01-10-2026.md`) e anote enquanto estuda.
3. Faça a prática na pasta do tema (ex.: `01-sql/exercicios/02-joins.sql`).
4. O que ficar claro de vez vai para o `README.md` do tema (a sua cola consolidada).
5. Salve no GitHub:
   ```bash
   git add .
   git commit -m "feat(sql): exercícios de JOIN"
   git push
   ```
6. **Noite (21:00–22:00):** releia a anotação e reveja os vídeos da manhã do dia de estudo anterior. Não precisa criar arquivo.

### Primeiro dia (01/10)
1. Aula de Git: `git init`, primeiro commit e criação do repositório no GitHub.
2. Criar `diario/git/GIT-01-10-2026.md` e anotar.
3. Preencher a tabela do `00-git/README.md` com os comandos aprendidos.
4. Noite: conferir as ferramentas instaladas (Git, Node, VS Code, Docker Desktop, DBeaver, Postman) e reler a manhã.
