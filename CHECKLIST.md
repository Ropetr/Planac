# 📋 CHECKLIST DE DOCUMENTAÇÃO - ERP PLANAC

> Controle de progresso de todos os documentos necessários para desenvolvimento do sistema.

---

## 📊 Resumo Geral

| Fase | Total | ✅ Feito | 🟡 Parcial | ⏳ Fazer |
|------|-------|---------|-----------|---------|
| **1 - Negócio** | 6 | 1 | 2 | 3 |
| **2 - Funcional** | 6 | 0 | 5 | 1 |
| **3 - Técnica** | 7 | 0 | 3 | 4 |
| **4 - Implantação** | 5 | 0 | 1 | 4 |
| **TOTAL** | **24** | **1** | **11** | **12** |

---

## 📘 FASE 1 - DOCUMENTAÇÃO DE NEGÓCIO
> O QUE o sistema deve fazer

| # | Documento | Descrição | Status | Link |
|---|-----------|-----------|--------|------|
| 1.1 | **Sumário Geral** | Estrutura de módulos e submódulos (23 capítulos) | ✅ Feito | [Ver](./docs/01-sumario/README.md) |
| 1.2 | **Regras de Negócio** | Todas as regras por módulo | 🟡 Parcial | [Ver](./docs/02-regras-negocio/README.md) |
| 1.3 | **Casos de Uso** | Fluxos completos por funcionalidade | 🟡 Parcial | [Ver](./docs/03-casos-uso/README.md) |
| 1.4 | **Histórias de Usuário** | Descrição do ponto de vista do usuário | ⏳ Fazer | - |
| 1.5 | **Glossário de Termos** | Definição de termos (CFOP, ST, Kit, etc.) | ⏳ Fazer | [Ver](./docs/10-anexos/glossario.md) |
| 1.6 | **Matriz de Permissões** | Quem pode fazer o quê em cada módulo | ⏳ Fazer | - |

### Detalhes do que já foi definido:

**1.2 - Regras de Negócio (Parcial):**
- ✅ Vendas: Bonificação, Financeiro flexível, Créditos, Limite
- ✅ Orçamentos: Mesclar, Desmembrar, Preço duplicado
- ✅ Estoque: Kit virtual vs montado
- ✅ Indicações: Crédito, validade, uso

**1.3 - Casos de Uso (Parcial):**
- ✅ Venda com entregas fracionadas
- ✅ Venda com faturamento parcial
- ✅ Orçamento mesclar/desmembrar
- ✅ Devoluções e Trocas

---

## 📗 FASE 2 - DOCUMENTAÇÃO FUNCIONAL
> COMO o sistema funciona

| # | Documento | Descrição | Status | Link |
|---|-----------|-----------|--------|------|
| 2.1 | **Fluxogramas de Processo** | Diagramas visuais de cada fluxo | 🟡 Parcial | [Ver](./docs/04-fluxogramas/README.md) |
| 2.2 | **Wireframes / Protótipos** | Esboço de cada tela do sistema | 🟡 Parcial | - |
| 2.3 | **Especificação de Telas** | Campos, validações, máscaras | 🟡 Parcial | [Ver](./docs/06-especificacao-telas/README.md) |
| 2.4 | **Relatórios e Dashboards** | Lista de todos os relatórios | ⏳ Fazer | - |
| 2.5 | **Notificações e Alertas** | Quais alertas, quando disparam | 🟡 Parcial | - |
| 2.6 | **Parâmetros do Sistema** | Configurações parametrizáveis | 🟡 Parcial | - |

### Detalhes do que já foi definido:

**2.1 - Fluxogramas (Parcial):**
- ✅ Fluxo de venda com entregas fracionadas (ASCII)

**2.3 - Especificação de Telas (Parcial):**
- ✅ Tela de uso de crédito na venda
- ✅ Tela de financeiro da venda
- ✅ Campos de bonificação

**2.5 - Notificações (Parcial):**
- ✅ Alerta de pedido X dias sem faturar
- ✅ Alerta de limite estourado
- ✅ Alerta de crédito disponível

**2.6 - Parâmetros (Parcial):**
- ✅ Regra de preço duplicado (mesclar orçamentos)

---

## 📙 FASE 3 - DOCUMENTAÇÃO TÉCNICA
> COMO construir o sistema

| # | Documento | Descrição | Status | Link |
|---|-----------|-----------|--------|------|
| 3.1 | **Arquitetura do Sistema** | Stack, infraestrutura, microserviços | 🟡 Parcial | [Ver](./docs/10-anexos/arquitetura.md) |
| 3.2 | **Modelo de Dados (DER)** | Diagrama Entidade-Relacionamento | ⏳ Fazer | [Ver](./docs/05-modelo-dados/README.md) |
| 3.3 | **Dicionário de Dados** | Tabelas, campos, tipos | ⏳ Fazer | - |
| 3.4 | **APIs e Endpoints** | Documentação de APIs | ⏳ Fazer | [Ver](./docs/07-apis/README.md) |
| 3.5 | **Integrações Externas** | NF-e, bancos, WhatsApp, etc. | 🟡 Parcial | [Ver](./docs/08-integracoes/README.md) |
| 3.6 | **Regras de Cálculo** | Fórmulas (impostos, comissões) | ⏳ Fazer | - |
| 3.7 | **Segurança** | Autenticação, criptografia, LGPD | 🟡 Parcial | - |

### Detalhes do que já foi definido:

**3.1 - Arquitetura (Parcial):**
- ✅ Stack sugerida: React, Cloudflare Workers, D1

**3.5 - Integrações (Parcial):**
- ✅ Lista: NF-e, NFC-e, CT-e, NFS-e, Bancos, PIX, WhatsApp, Google, Meta

**3.7 - Segurança (Parcial):**
- ✅ 2FA opcional
- ✅ LGPD mencionado

---

## 📕 FASE 4 - DOCUMENTAÇÃO DE IMPLANTAÇÃO
> COMO colocar em produção

| # | Documento | Descrição | Status | Link |
|---|-----------|-----------|--------|------|
| 4.1 | **Roadmap de Implementação** | Ordem de desenvolvimento | 🟡 Parcial | [Ver](./docs/10-anexos/roadmap.md) |
| 4.2 | **Plano de Migração** | Migrar dados do sistema atual | ⏳ Fazer | - |
| 4.3 | **Plano de Testes** | Casos de teste por funcionalidade | ⏳ Fazer | - |
| 4.4 | **Manual do Usuário** | Documentação para usuário final | ⏳ Fazer | [Ver](./docs/09-manuais/usuario.md) |
| 4.5 | **Manual do Administrador** | Configurações e manutenção | ⏳ Fazer | [Ver](./docs/09-manuais/admin.md) |

### Detalhes do que já foi definido:

**4.1 - Roadmap (Parcial):**
- ✅ 5 fases de implantação sugeridas

---

## 🚀 Ordem Sugerida de Criação

```
1️⃣ Sumário Geral (1.1) ✅ FEITO
   └── Estrutura de módulos e submódulos

2️⃣ Regras de Negócio (1.2) ← PRÓXIMO
   └── Consolidar TODAS as regras já definidas
   └── Adicionar regras faltantes

3️⃣ Casos de Uso (1.3)
   └── Fluxos completos passo a passo

4️⃣ Fluxogramas (2.1)
   └── Diagramas visuais dos processos

5️⃣ Modelo de Dados (3.2)
   └── Estrutura do banco de dados

6️⃣ Especificação de Telas (2.3)
   └── Detalhe de cada campo
```

---

## 📅 Histórico de Atualizações

| Data | Autor | Alteração |
|------|-------|-----------|
| 28/11/2025 | Claude AI | Criação inicial do checklist |

---

*Atualizado em: 28/11/2025*
