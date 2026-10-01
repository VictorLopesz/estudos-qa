# 00 · MCP + IA para QA

## Objetivo
Usar o MCP (Model Context Protocol) e o Claude Code no trabalho de QA, sempre com revisão humana: explorar telas, gerar casos e testes, consultar o banco em modo somente leitura, abrir bugs e criar um servidor MCP próprio em TypeScript.

## 📂 Estrutura (vai sendo criada nas aulas)
- `exploracao-serverest.md` — cenários sugeridos pelo Playwright MCP + a sua revisão
- `casos-gerados.md` — casos/Gherkin gerados pela IA x revisão humana
- `mysql-mcp.md` — MCP do MySQL com usuário só de leitura
- `seguranca.md` — checklist antes de instalar um servidor MCP
- `servidor-massa/` — o seu servidor MCP em TypeScript

## 📒 Cola de comandos
> Preencha conforme for estudando.

| Comando | Para que serve |
|---|---|
| `claude mcp list` | Lista os servidores MCP configurados |

## 🔐 Regras
- Tokens e senhas só em variáveis de ambiente, nunca no `.mcp.json` que vai para o GitHub
- Banco via MCP: usuário só com `SELECT`
- Tudo que a IA gerar passa pela sua revisão antes de entrar no repositório

## ✅ O que aprendi
-
