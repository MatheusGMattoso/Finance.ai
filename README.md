# Finance.ai - Dashboard Financeiro Inteligente

## 1. Visão Geral
O Finance.ai é uma plataforma SaaS de gestão financeira pessoal que utiliza Inteligência Artificial para categorizar transações e oferecer insights de economia. O objetivo é permitir que usuários acompanhem múltiplas contas (bancárias, carteira, investimentos) em tempo real.

## 2. Tech Stack (Padrão de Mercado 2024)
- **Frontend:** Next.js 14 (App Router), React, TailwindCSS, Shadcn/UI.
- **Backend:** Next.js Server Actions (API-less architecture).
- **Database:** PostgreSQL (via NeonDB ou Supabase).
- **ORM:** Prisma.
- **Validação:** Zod + React Hook Form.
- **AI Integration:** OpenAI API (para insights de gastos).

## 3. Funcionalidades do MVP (Escopo Inicial)
### 3.1. Autenticação & Usuários
- [x] Login Social (Google) via NextAuth/Clerk.
- [x] Proteção de rotas (Middleware).

### 3.2. Gestão de Transações
- [ ] CRUD completo de transações (Receitas e Despesas).
- [ ] Uso de `Decimal` para precisão monetária.
- [ ] Datepickers e Inputs monetários mascarados.

### 3.3. Dashboard & Visualização
- [ ] Resumo do Mês (Cards de Receita, Despesa, Saldo).
- [ ] Gráfico de Barras (Gastos por dia/semana).
- [ ] Gráfico de Rosca (Gastos por categoria).

### 3.4. IA (Diferencial)
- [ ] Botão "Gerar Relatório IA": Analisa as transações do mês e sugere onde economizar.

## 4. Arquitetura de Dados (High Level)
O banco de dados é Relacional (SQL) para garantir ACID.
Principais Entidades: `User` -> `Account` -> `Transaction` -> `Category`.

## 5. Regras de Negócio (Non-negotiables)
- Uma transação não pode existir sem um usuário.
- O saldo não é salvo no banco, é calculado via agregação (SUM) para evitar inconsistências.
- Tipos monetários devem ser tratados como `Decimal` no Backend e formatados apenas no Frontend `Intl.NumberFormat`.
