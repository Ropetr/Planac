# SUMÁRIO GERAL - ERP PLANAC

Sistema ERP Completo | Multi-Empresas | Atacado, Varejo e Atacarejo

Versão 2.0 - Estrutura Reorganizada | 23 Capítulos + 4 Anexos

---

## Índice Geral

| Parte | Nome | Capítulos |
|:-----:|:-----|:---------:|
| **1** | Módulos Core | 01-03 |
| **2** | Módulo Comercial | 04 |
| **3** | Módulo Compras | 05 |
| **4** | Módulos Financeiros | 06-09 |
| **5** | Módulos Fiscais | 10-12 |
| **6** | Separação e Expedição | 13 |
| **7** | Módulos de Inteligência | 14 |
| **8** | Módulos de Marketing, E-commerce e Atendimento | 15-17 |
| **9** | Módulos de Integração | 18-19 |
| **10** | Módulos de Interface | 20-21 |
| **11** | Módulos de Suporte | 22-23 |
| **12** | Recursos Humanos | 24 |
| **-** | Anexos | A-D |

---

## PARTE 1 - MÓDULOS CORE (Fundamentais)

### Capítulo 01 - Gestão de Empresas e Multi-Tenant

- Cadastro de múltiplas empresas/filiais
- Configurações fiscais por empresa (CNPJ, IE, regime tributário)
- Permissões e acessos por empresa
- Consolidação de dados entre empresas
- Parâmetros individuais por empresa

### Capítulo 02 - Cadastros Base

**Clientes (PF/PJ) com integração API CNPJ/CPF:**

- Vendedor padrão do cliente
- Quem indicou (vínculo com Programa de Indicações)
- Múltiplos endereços e contatos
- Tipos: Consumidor, Construtora, Instalador, Revendedor

**Fornecedores:**

- Cadastro completo de fornecedores
- Histórico de compras
- Avaliação de fornecedores

**Produtos e serviços:**

- Categorias e subcategorias
- NCM, CEST, origem
- Múltiplas fotos
- Especificações técnicas

**Produto Kit:**

- Composição (produtos e quantidades)
- Tipo: Virtual (baixa componentes) ou Montado (estoque próprio)
- Precificação: Soma dos itens ou preço promocional
- Foto do kit montado

**Unidades de medida:**

- Cadastro de unidades
- Conversão entre unidades

**Tabelas de preço (atacado/varejo):**

- Preço por quantidade (atacarejo)
- Vigência

### Capítulo 03 - Gestão de Usuários e Permissões

- Controle de acesso por módulo
- Perfis de usuário (admin, vendedor, financeiro, etc.)
- Log de atividades/auditoria
- Autenticação segura (2FA opcional)
- Sessões e dispositivos autorizados

---

## PARTE 2 - MÓDULO COMERCIAL

### Capítulo 04 - Comercial (9 Submódulos)

**Menu da Interface:**

```
COMERCIAL
├── CRM
├── CalcPro
├── Orçamentos
├── Pedido de Venda
├── PDV
├── Programa de Indicações
├── Devolução de Venda
├── Troca de Venda
└── Serviços
```

---

#### 4.1 - CRM (Gestão de Relacionamento)

- Funil de vendas
- Pipeline de oportunidades
- Histórico de interações
- Tarefas e follow-ups
- Segmentação de clientes
- Análise de conversão

#### 4.2 - CalcPro (Calculadoras de Sistemas Construtivos)

- Calculadora de Drywall
- Calculadora de Steel Frame
- Calculadora de Forro
- Calculadora de Revestimento
- Geração automática de lista de materiais
- Conversão em orçamento

#### 4.3 - Orçamentos

**Funcionalidades Básicas:**

- Criação de orçamentos
- Validade do orçamento
- Conversão em pedido de venda
- Histórico de orçamentos por cliente
- Versionamento de orçamentos
- Aprovação de orçamentos
- Envio por email/WhatsApp
- Impressão personalizada

**Mesclar Orçamentos:**

- Seleção múltipla de orçamentos
- Permite mesclar de clientes diferentes
- Alteração do cliente no orçamento principal
- Soma automática de itens iguais
- Regra de preço duplicado parametrizável pelo Admin (menor preço, maior preço, mais recente ou manual)
- Geração de orçamento principal
- Dropdown com orçamentos mesclados vinculados
- Permite mesclar orçamentos já mesclados
- Desmesclar: voltar aos orçamentos originais

**Desmembrar Orçamentos:**

- Seleção de itens para separar
- Funciona em orçamentos mesclados e não mesclados
- Numeração sequencial: #1236.1, #1236.2, #1236.3...
- Vínculo com orçamento pai
- Dropdown com orçamentos filhos (desmembrados)
- Rastreabilidade completa

#### 4.4 - Pedido de Venda

**Funcionalidades Básicas:**

- Pedidos de venda (atacado e varejo)
- Venda direta (sem orçamento) ou conversão de orçamento
- Regras de preço por quantidade (atacarejo)
- Descontos progressivos
- Comissões de vendedores
- Metas de vendas
- Histórico de negociações
- Aprovação de descontos

**Checkbox Bonificado:**

- CFOP automático (5.910/6.910)
- Campo obrigatório: Motivo da bonificação
- Não gera financeiro (contas a receber)
- Aprovação por alçada específica
- Limite de bonificação por período (parametrizável)
- Relatório de bonificações

**Status do Pedido:**

- Aberto (criado, nada faturado/entregue)
- Parcialmente Faturado (algumas NFs emitidas)
- Totalmente Faturado (100% com NF)
- Parcialmente Entregue (algumas entregas feitas)
- Totalmente Entregue (tudo entregue)
- Finalizado (100% faturado + 100% entregue)

**Controle de Entregas/Retiradas:**

- Registro de entregas fracionadas (.E1, .E2, .E3...)
- Tipo: Retirada pelo cliente ou Entrega
- Itens e quantidades por entrega
- Responsável (quem retirou / motorista)
- Vinculação com NF (se emitida)
- Status: Com NF / Sem NF / Consumidor Final
- Histórico completo de movimentações

**Faturamento Flexível:**

- Faturar total (NF de tudo)
- Faturar parcial (seleciona itens/quantidades)
- Faturar por entrega (NF só do que foi na .E1, .E2...)
- Trocar destinatário da NF (emitir em outro CPF/CNPJ)
- Consolidar pedidos em uma NF (juntar A + B + C)
- NF Consumidor Final (não identificado)
- Painel de faturamento pendente
- Alerta de pedidos há X dias sem faturar

**Controle Financeiro da Venda:**

- Opção 1: Recebimento Integral (baixa total na hora)
- Opção 2: Contas a Receber na Venda Pai (parcelas no pedido principal)
- Opção 3: Financeiro por Entrega (gera financeiro em cada .E1, .E2...)
- Opção 4: Sem Financeiro Agora (define depois na entrega)

**Múltiplas Formas de Pagamento:**

- Combinar formas na mesma entrega (PIX + Cartão + Crédito)
- Formas diferentes por entrega
- Parcelamento por forma de pagamento
- Integração automática com Contas a Receber

**Uso de Crédito do Cliente:**

- Alerta automático de crédito disponível na venda
- Opção: Usar crédito na Venda Pai
- Opção: Reservar crédito para Entregas Fracionadas
- Opção: Não usar crédito agora
- Uso parcial do crédito
- Combinar crédito com outras formas de pagamento
- Tipos de crédito: Indicação, Devolução, Bonificação, Adiantamento
- Carteira unificada de créditos do cliente
- Histórico de uso de créditos

**Limite de Crédito:**

- Compromete limite na venda (mesmo sem faturar)
- Libera limite conforme recebimento
- Alerta de estouro de limite
- Bloqueio de venda por limite excedido (parametrizável)

**Desmembrar Vendas:**

- Separar pedido em múltiplos (#1000.1, #1000.2...)
- Seleção de itens para separar
- Funciona igual orçamento
- Rastreabilidade com pedido pai
- Dropdown com vendas filhas

**Visão Consolidada da Venda:**

- Total da venda
- Valor faturado
- Valor entregue
- Valor recebido
- Valor a receber
- Crédito utilizado
- Valor pendente (sem financeiro definido)

**Relatórios de Vendas:**

- Vendas por período
- Vendas por vendedor
- Vendas por cliente
- Faturamento pendente
- Entregas pendentes
- Itens mais vendidos
- Ticket médio
- Conversão orçamento para venda

#### 4.5 - PDV (Ponto de Venda)

- Frente de caixa para varejo
- Integração com balanças e leitores
- Sangria e suprimento de caixa
- Fechamento de caixa
- TEF (cartões de crédito/débito)
- Múltiplas formas de pagamento
- Cupom fiscal eletrônico (NFC-e)
- Gaveta de dinheiro
- Uso de crédito de indicação no PDV
- Consulta de crédito disponível do cliente

#### 4.6 - Programa de Indicações

**Configuração:**

- Quem pode indicar: Cliente ou Parceiro Externo
- Tipo de benefício: Dinheiro ou Crédito na Loja
- Percentual ou valor fixo por indicação
- Aplicar sobre: 1ª Compra ou Todas as Compras
- Momento do crédito: Imediato ou Após Recebimento
- Validade do crédito (dias)
- Limite máximo de crédito por indicação

**Funcionalidades:**

- Cadastro de indicadores
- Vínculo cliente com indicador
- Geração automática de crédito
- Carteira de créditos do cliente
- Uso do crédito em vendas e PDV
- Relatório de indicações
- Ranking de indicadores

#### 4.7 - Devolução de Venda

Cliente devolvendo produto que comprou:

- NF-e de Entrada (devolução)
- Entrada no estoque
- Financeiro: Estorno ou crédito para cliente
- Motivo da devolução (obrigatório)
- Aprovação por alçada
- Vínculo com venda original
- Geração de crédito na carteira do cliente

#### 4.8 - Troca de Venda

Cliente troca produto por outro:

- Devolução + Nova Venda (2 NF-e)
- Entra produto devolvido, sai novo produto
- Diferença a pagar ou receber
- Aprovação por alçada
- Rastreabilidade completa

#### 4.9 - Serviços

- Ordem de Serviço (OS)
- Agendamento de Serviços
- Controle de Técnicos/Equipes
- Checklist de Execução
- Apontamento de Horas
- Materiais Utilizados
- Assinatura Digital do Cliente
- Histórico de Serviços por Cliente
- SLA e Prazos
- NFS-e (Nota Fiscal de Serviço)

---

## PARTE 3 - MÓDULO COMPRAS

### Capítulo 05 - Compras (11 Submódulos)

**Menu da Interface:**

```
COMPRAS
├── Cotações com Fornecedores
├── Pedido de Compra
├── Recebimento de Mercadorias
├── Devolução de Compra
├── Troca de Compra
├── Importação de Documentos (NF-e, NFS-e, CT-e)
├── Análise de Preços por Fornecedor
├── Estoque
├── WMS (Gestão de Armazém)
├── Produção / PCP
└── Gestão de Kits
```

---

#### 5.1 - Cotações com Fornecedores

- Solicitação de cotação
- Comparativo de preços
- Aprovação de melhor oferta
- Histórico de cotações

#### 5.2 - Pedido de Compra

- Criação de pedidos
- Checkbox Bonificado (recebimento de bonificação de fornecedor)
- Aprovação por alçada
- Acompanhamento de status
- Vínculo com cotação

#### 5.3 - Recebimento de Mercadorias

- Conferência física vs NF
- Entrada no estoque
- Divergências (faltas, sobras, avarias)
- Etiquetagem
- Lote e validade

#### 5.4 - Devolução de Compra

Devolvendo produto ao fornecedor:

- NF-e de Saída (devolução)
- Saída do estoque
- Financeiro: Estorno ou crédito do fornecedor
- Motivo da devolução

#### 5.5 - Troca de Compra

Trocando produto com fornecedor:

- Devolução + Nova Entrada
- Rastreabilidade completa

#### 5.6 - Importação de Documentos Fiscais

- Importação de NF-e (mercadorias)
- Importação de NFS-e (serviços)
- Importação de CT-e (transporte)
- Manifestação do destinatário
- Vinculação com pedido de compra

#### 5.7 - Análise de Preços por Fornecedor

- Histórico de preços
- Curva de preço
- Comparativo entre fornecedores
- Sugestão de compra

#### 5.8 - Estoque

- Controle de estoque por empresa/filial
- Estoque mínimo/máximo
- Inventário físico
- Transferência entre filiais
- Controle de lote e validade
- Curva ABC
- Reserva de estoque (na venda, mesmo sem faturar)
- Rastreabilidade

#### 5.9 - WMS (Gestão de Armazém)

- Endereçamento de estoque
- FIFO/FEFO
- Conferência por código de barras
- Inventário rotativo
- Cross-docking
- Mapa do armazém

#### 5.10 - Produção / PCP

- Ordem de Produção
- Ficha Técnica (BOM - Bill of Materials)
- Roteiro de Fabricação
- Apontamento de Produção
- Controle de Insumos
- Custo de Produção
- Capacidade Produtiva
- Rastreabilidade de Lotes

#### 5.11 - Gestão de Kits

- Montagem de kits
- Desmontagem de kits
- Baixa automática de componentes (kit virtual)
- Alerta de componente em falta
- Custo do kit

---

## PARTE 4 - MÓDULOS FINANCEIROS

### Capítulo 06 - Contas a Receber

- Títulos e parcelas
- Boletos (integração bancária)
- PIX (integração)
- Cartões (conciliação)
- Cobrança automatizada
- Régua de cobrança
- Renegociação
- Baixa automática
- Carteira de créditos do cliente

### Capítulo 07 - Contas a Pagar

- Títulos a pagar
- Agendamento de pagamentos
- Pagamento em lote
- Integração bancária (CNAB)
- Aprovação por alçada

### Capítulo 08 - Fluxo de Caixa

- Visão diária/semanal/mensal
- Projeção de caixa
- DRE gerencial
- Centro de custos
- Conciliação bancária

### Capítulo 09 - Bancos e Tesouraria

- Cadastro de contas bancárias
- Movimentações
- Transferências entre contas
- Integração Open Banking

---

## PARTE 5 - MÓDULOS FISCAIS

### Capítulo 10 - Fiscal / Tributário

- Configuração de NCM/CEST
- Regras de ICMS por estado (ST, diferencial de alíquota)
- PIS/COFINS
- IPI
- Benefícios fiscais
- CFOP automático

### Capítulo 11 - Documentos Fiscais

- Emissão NF-e
- Emissão NFC-e (varejo)
- Emissão NFS-e (serviços)
- CT-e (transporte próprio)
- Carta de Correção
- Cancelamento
- Inutilização

### Capítulo 12 - Obrigações Acessórias

- SPED Fiscal
- SPED Contribuições
- EFD-Reinf
- DCTF

---

## PARTE 6 - SEPARAÇÃO E EXPEDIÇÃO

### Capítulo 13 - Separação e Expedição

- Separação de pedidos (picking)
- Conferência de itens
- Romaneio de carga
- Etiquetas de volume
- Roteirização de entregas
- Controle de frota
- Integração com transportadoras
- Cálculo de frete
- Registro de entregas fracionadas (.E1, .E2...)

**App do Motorista/Entregador:**

- Login do motorista
- Lista de entregas do dia
- Roteiro otimizado (Waze/Google Maps)
- GPS em tempo real (compartilhado com cliente)
- Check-in na entrega (chegou no local)
- Foto do comprovante de entrega
- Assinatura digital do recebedor
- Registro de ocorrências (ausente, recusado, endereço errado)
- Baixa automática da entrega
- Notificação automática para o cliente

---

## PARTE 7 - MÓDULOS DE INTELIGÊNCIA

### Capítulo 14 - BI e Dashboards

- Dashboards personalizáveis
- KPIs por módulo
- Relatórios gerenciais
- Exportação de dados
- Análise de tendências
- Comparativos (período, filial, vendedor)

---

## PARTE 8 - MÓDULOS DE MARKETING, E-COMMERCE E ATENDIMENTO

### Capítulo 15 - OmniPro (Atendimento Multicanal)

- WhatsApp Business API
- Instagram Direct
- Facebook Messenger
- Chat do site
- Chatbot com IA
- Fila de atendimento
- Histórico unificado
- Transferência entre atendentes

### Capítulo 16 - E-commerce (B2B + B2C)

**16.1 - Configurações Gerais:**

- Domínio e SSL
- Identidade visual (logo, cores, fontes)
- Páginas institucionais (Sobre, Contato, etc.)
- Políticas (privacidade, troca, entrega)
- SEO básico (meta tags, sitemap, robots)
- Blog integrado

**16.2 - Catálogo de Produtos:**

- Sincronização automática com cadastro do ERP
- Categorias e subcategorias
- Filtros avançados (marca, preço, características)
- Múltiplas fotos e vídeos por produto
- Especificações técnicas detalhadas
- Produtos relacionados e similares
- Kits e combos
- Produtos sob consulta (sem preço visível)
- Estoque em tempo real
- Avise-me quando chegar

**16.3 - Vitrine B2C (Consumidor Final):**

- Cadastro simplificado (CPF, e-mail, telefone)
- Preço de varejo
- Carrinho de compras
- Lista de desejos
- Avaliações e comentários de produtos
- Comparador de produtos

**16.4 - Portal B2B (Atacado/Revenda):**

- Cadastro com aprovação prévia (CNPJ)
- Análise de crédito integrada
- Aprovação de pedido por alçada (mesmo com crédito aprovado)
- Tabelas de preço por cliente/grupo
- Quantidade mínima por produto
- Desconto progressivo por volume
- Pedido mínimo (valor ou quantidade)
- Limite de crédito visível no painel
- Saldo de crédito (indicações, devoluções)
- Vendedor vinculado ao cliente
- Cotação online (solicitar orçamento)
- Pedido recorrente (repetir último pedido)
- Múltiplas listas de compras salvas
- Histórico de compras e preços
- Download de XML das notas fiscais
- Múltiplos endereços de entrega

**16.5 - Área do Cliente (Minha Conta):**

- Meus pedidos (status, histórico completo)
- Rastreamento de entregas
- Rastreamento em tempo real no mapa (GPS do motorista)
- Previsão de chegada atualizada
- Segundas vias de boletos
- Minhas notas fiscais (download XML/PDF)
- Meus orçamentos/cotações
- Meu limite de crédito (B2B)
- Meu saldo de créditos (indicações, devoluções)
- Meus endereços
- Meus dados cadastrais
- Minhas listas de compras (B2B)
- Repetir pedido anterior
- Abrir chamado/suporte
- Histórico de atendimentos
- Programa de indicação (meu link, minhas indicações)
- Trocar senha
- Preferências de notificação

**16.6 - Área do Vendedor/Representante:**

- Login como representante
- Selecionar cliente para fazer pedido
- Ver carteira de clientes
- Acompanhar pedidos dos clientes
- Comissões a receber
- Metas e performance

**16.7 - Formas de Pagamento:**

- Checkout transparente
- PIX (com QR Code e copia/cola)
- Cartão de crédito (parcelado)
- Cartão de débito
- Boleto bancário
- Duas ou mais formas combinadas
- Uso de crédito do cliente (indicação, devolução)

**Exclusivo B2B:**

- Faturamento (28/35/42/56 dias)
- Boleto parcelado
- Cartão corporativo

**16.8 - Frete e Logística:**

- Integração com Correios
- Integração com transportadoras
- Tabela de frete própria
- Frete grátis (regras configuráveis por valor/região)
- Retirada na loja/CD
- Entrega agendada
- Frete CIF / FOB (B2B)
- Rastreamento integrado (código de rastreio)
- Rastreamento em tempo real no mapa (Google Maps)
- GPS dos motoristas/entregadores
- Notificação automática (saiu para entrega, chegando)
- Múltiplos CDs (estoque por região)

**16.9 - Recuperação e Conversão:**

- Carrinho abandonado (e-mail automático)
- Cupons de desconto
- Promoções (compre X leve Y, desconto progressivo)
- Banners rotativos
- Vitrines personalizadas (mais vendidos, lançamentos)
- Pop-ups de captura (primeira compra)
- Contador de urgência (promoção por tempo limitado)

**16.10 - Integrações:**

- Sincronização com ERP PLANAC (estoque, preços, pedidos, clientes)
- Marketplaces (estrutura preparada para futuro)
  - Mercado Livre
  - Amazon
  - Shopee
  - Magalu
- Google Shopping / Merchant Center
- Facebook/Instagram Shopping
- Comparadores de preço (Buscapé, Zoom)
- WhatsApp (botão flutuante e notificações)
- Google Analytics / Tag Manager
- Meta Pixel (Facebook/Instagram Ads)

**16.11 - Relatórios e Analytics:**

- Vendas por período
- Vendas por categoria/produto
- Produtos mais vendidos
- Clientes que mais compram
- Carrinho abandonado (taxa e valor)
- Taxa de conversão
- Origem do tráfego
- Ticket médio
- Novos clientes vs recorrentes
- Dashboard em tempo real

**16.12 - App Mobile (PWA):**

- Versão responsiva otimizada
- Progressive Web App (instalar na tela inicial)
- Notificações push
- Navegação offline (catálogo em cache)

### Capítulo 17 - Google e Meta

**Google:**

- Analytics
- Tag Manager
- Search Console
- Merchant Center
- Google Ads
- Google Meu Negócio

**Meta:**

- Ads Manager
- Conversions API (CAPI)
- Catálogo de produtos
- Lookalike audiences
- Instagram Shopping

---

## PARTE 9 - MÓDULOS DE INTEGRAÇÃO

### Capítulo 18 - Integrações Externas

- E-commerce (Magento, WooCommerce, VTEX)
- Marketplaces (Mercado Livre, Amazon, Shopee)
- APIs de consulta (CNPJ, CEP, IBGE)
- Gateways de pagamento
- Contabilidade (exportação)
- ERP legado (migração)

### Capítulo 19 - Automação e Workflows

- Regras de negócio automatizadas
- Notificações e alertas (email, SMS, push)
- Aprovações em cadeia
- Agendamento de tarefas
- Webhooks personalizados
- Filas de processamento

---

## PARTE 10 - MÓDULOS DE INTERFACE

### Capítulo 20 - Portal do Cliente

(Funcionalidades migradas para o Capítulo 16 - E-commerce, seção 16.5 - Área do Cliente)

O acesso do cliente ao portal acontece através do mesmo login do E-commerce, na área "Minha Conta".

### Capítulo 21 - App Mobile (Força de Vendas)

- Cadastro de clientes em campo
- Pedidos offline (sincronização)
- Consulta de estoque/preços
- Roteiro de visitas
- Catálogo digital
- Assinatura na entrega
- GPS e check-in

---

## PARTE 11 - MÓDULOS DE SUPORTE

### Capítulo 22 - Configurações do Sistema

- Parâmetros gerais
- Personalização de campos
- Numeração de documentos
- Backup e restauração
- Logs do sistema
- Importação/exportação de dados

**Configurações específicas:**

- Regra de preço duplicado (mesclar orçamentos)
- Limite de bonificação
- Validade de crédito de indicação
- Dias para alerta de faturamento pendente

### Capítulo 23 - Central de Ajuda

- Documentação do sistema
- Tutoriais em vídeo
- Chat de suporte
- Tickets de atendimento
- Base de conhecimento
- Atualizações do sistema

---

## PARTE 12 - RECURSOS HUMANOS

### Capítulo 24 - Gestão de RH

**24.1 - Cadastro de Colaboradores:**

- Dados pessoais (nome, CPF, RG, endereço)
- Dados contratuais (cargo, departamento, data admissão)
- Documentos digitalizados
- Dependentes
- Dados bancários
- Histórico de cargos/salários
- Foto do colaborador

**24.2 - Estrutura Organizacional:**

- Departamentos e setores
- Cargos e funções
- Hierarquia (organograma)
- Centros de custo por departamento

**24.3 - Controle de Ponto:**

- Registro de ponto (entrada, saída, intervalos)
- Ponto eletrônico integrado
- Ponto pelo App do Colaborador
- Ponto por geolocalização (externo)
- Banco de horas
- Horas extras
- Faltas e atrasos
- Abonos
- Espelho de ponto
- Fechamento mensal

**24.4 - Férias e Afastamentos:**

- Programação de férias
- Saldo de férias
- Solicitação de férias (pelo app)
- Aprovação de férias
- Afastamentos (atestado, licenças)
- Controle de atestados médicos

**24.5 - Folha de Pagamento:**

- Cálculo automático de salários
- Horas extras e adicionais
- Descontos (INSS, IRRF, VT, VR, faltas)
- Benefícios
- Comissões (integração com vendas)
- 13º salário
- Rescisão
- Geração de holerites
- Integração contábil

**24.6 - Benefícios:**

- Vale transporte
- Vale refeição/alimentação
- Plano de saúde
- Plano odontológico
- Seguro de vida
- Outros benefícios

**24.7 - Recrutamento e Seleção:**

- Banco de currículos
- Vagas abertas
- Candidaturas
- Triagem de currículos
- Agendamento de entrevistas
- Avaliação de candidatos
- Histórico de processos seletivos

**24.8 - Treinamentos:**

- Cadastro de treinamentos
- Programação de treinamentos
- Inscrições
- Lista de presença
- Certificados
- Histórico por colaborador
- Treinamentos obrigatórios (NR)

**24.9 - Avaliação de Desempenho:**

- Ciclos de avaliação
- Metas individuais
- Autoavaliação
- Avaliação do gestor
- Feedback 360º
- Plano de desenvolvimento individual (PDI)

**24.10 - App do Colaborador:**

- Login seguro (CPF + senha)
- Bater ponto pelo celular
- Ponto com geolocalização e foto
- Ver espelho de ponto
- Solicitar férias
- Solicitar abono/justificativa
- Ver holerites (PDF)
- Ver informe de rendimentos
- Atualizar dados cadastrais
- Enviar atestados médicos (foto)
- Ver escala de trabalho
- Ver comunicados da empresa
- Canal de denúncias (anônimo)
- Chat com RH
- Notificações push

---

## ANEXOS

### Anexo A - Arquitetura Técnica

Stack tecnológica, infraestrutura, servidores, banco de dados, APIs

### Anexo B - Modelo de Dados

Diagrama Entidade-Relacionamento, principais tabelas

### Anexo C - Glossário de Termos

Definições: CFOP, NCM, CEST, ST, NF-e, etc.

### Anexo D - Roadmap de Implementação

Fases de implantação, ordem de módulos, cronograma

---

## Resumo da Estrutura

| Info | Valor |
|------|-------|
| Total de Capítulos | 24 |
| Total de Partes | 12 |
| Total de Anexos | 4 |
| Submódulos COMERCIAL | 9 |
| Submódulos COMPRAS | 11 |
| Versão | 2.1 |

---

## Histórico de Versões

| Versão | Data | Alterações |
|--------|------|------------|
| 2.1 | 29/11/2025 | Adicionado: E-commerce B2B+B2C, RH com App do Colaborador, Rastreamento GPS |
| 2.0 | 28/11/2025 | Reorganização: 23 capítulos, menus COMERCIAL e COMPRAS |
| 1.0 | 28/11/2025 | Estrutura inicial: 34 capítulos |

---

PLANAC Distribuidora - Sistema ERP - Documentação Oficial
