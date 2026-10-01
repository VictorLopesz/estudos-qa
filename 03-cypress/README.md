# 03 · Cypress avançado (TypeScript)

## Objetivo
Testes E2E estáveis e bem organizados: Page Objects, custom commands tipados, cy.session, cy.intercept, fixtures, dados com Faker, sem esperas fixas.

## 🎯 Aplicação: [front.serverest.dev](https://front.serverest.dev)

## 📂 Estrutura (quando criar o projeto)
- `cypress/e2e/` — specs: só fluxo e validações
- `cypress/pages/` — Page Objects (seletores e ações)
- `cypress/support/commands.ts` + `index.d.ts` — custom commands tipados
- `cypress/fixtures/` — massa de dados e mocks
- `cypress.env.json` — credenciais (fora do git)

## 📐 Regras do projeto
- Seletores estáveis (`data-cy`, `data-testid`); nada de seletor solto nos specs
- Nunca `cy.wait(ms)`: esperar por elemento, asserção ou `cy.wait('@alias')`

## ✅ O que aprendi
-
