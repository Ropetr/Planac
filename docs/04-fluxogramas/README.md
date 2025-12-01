# 📊 Fluxogramas de Processo - ERP PLANAC

Diagramas visuais dos principais processos do sistema.

---

## Índice de Fluxogramas

| # | Fluxo | Módulo | Status |
|---|-------|--------|--------|
| 1 | Venda Completa (com entregas fracionadas) | Comercial | ✅ |
| 2 | Orçamento (mesclar/desmembrar) | Comercial | ✅ |
| 3 | Uso de Crédito na Venda | Comercial | ✅ |
| 4 | Devolução de Venda | Comercial | ✅ |
| 5 | Troca de Venda | Comercial | ✅ |
| 6 | Consignação | Comercial | ✅ |
| 7 | Compra Completa | Compras | ✅ |
| 8 | Fluxo Financeiro (Recebimento) | Financeiro | ✅ |
| 9 | E-commerce B2B | E-commerce | ✅ |
| 10 | E-commerce B2C | E-commerce | ✅ |
| 11 | Entrega com Rastreamento GPS | Expedição | ✅ |
| 12 | Garantia de Produtos | Comercial | ✅ |

---

## 1. Fluxo de Venda Completa

```mermaid
flowchart TD
    A[Início] --> B{Origem?}
    B -->|Orçamento| C[Converter Orçamento em Venda]
    B -->|Direta| D[Criar Venda Direta]
    
    C --> E[Venda Criada #1000]
    D --> E
    
    E --> F{Cliente tem crédito?}
    F -->|Sim| G[Perguntar se usa crédito]
    F -->|Não| H[Definir forma de pagamento]
    
    G --> G1{Opção escolhida?}
    G1 -->|Usar na Venda Pai| G2[Abater crédito do total]
    G1 -->|Reservar para Entregas| G3[Manter crédito reservado]
    G1 -->|Não usar| H
    
    G2 --> H
    G3 --> H
    
    H --> I{Tipo de financeiro?}
    I -->|Recebimento Integral| J[Baixa total na hora]
    I -->|Contas a Receber na Pai| K[Gera parcelas no pedido principal]
    I -->|Financeiro por Entrega| L[Define em cada entrega]
    I -->|Sem Financeiro Agora| M[Define depois]
    
    J --> N[Reserva Estoque]
    K --> N
    L --> N
    M --> N
    
    N --> O{Tipo de entrega?}
    O -->|Total| P[Entrega única]
    O -->|Fracionada| Q[Entregas parciais]
    
    P --> R[Registrar Entrega]
    Q --> S[Registrar Entrega .E1]
    
    R --> T{Faturar?}
    S --> T
    
    T -->|Sim| U[Emitir NF-e]
    T -->|Depois| V[Faturamento Pendente]
    
    U --> W{Mais entregas?}
    V --> W
    
    W -->|Sim| X[Registrar Entrega .E2, .E3...]
    W -->|Não| Y{Tudo entregue e faturado?}
    
    X --> T
    
    Y -->|Sim| Z[Venda Finalizada]
    Y -->|Não| AA[Venda Parcial - Acompanhar]
    
    Z --> AB[Fim]
    AA --> AB
```

---

## 2. Fluxo de Orçamento (Mesclar/Desmembrar)

```mermaid
flowchart TD
    A[Início] --> B[Criar Orçamento]
    B --> C[Orçamento #1236]
    
    C --> D{Ação?}
    
    D -->|Aprovar| E[Converter em Venda]
    D -->|Mesclar| F[Selecionar outros orçamentos]
    D -->|Desmembrar| G[Selecionar itens para separar]
    D -->|Editar| H[Alterar itens/valores]
    D -->|Cancelar| I[Orçamento Cancelado]
    
    F --> J{Clientes diferentes?}
    J -->|Sim| K[Escolher cliente principal]
    J -->|Não| L[Manter cliente]
    
    K --> M[Mesclar orçamentos]
    L --> M
    
    M --> N{Itens duplicados?}
    N -->|Sim| O{Regra de preço?}
    N -->|Não| P[Orçamento Mesclado]
    
    O -->|Menor preço| Q[Usar menor valor]
    O -->|Maior preço| R[Usar maior valor]
    O -->|Mais recente| S[Usar último]
    O -->|Manual| T[Usuário escolhe]
    
    Q --> P
    R --> P
    S --> P
    T --> P
    
    P --> U[Orçamento Principal com dropdown de mesclados]
    
    G --> V[Criar orçamentos filhos]
    V --> W[#1236.1, #1236.2...]
    W --> X[Orçamentos vinculados ao pai]
    
    H --> C
    
    E --> Y[Venda Criada]
    U --> D
    X --> D
    
    Y --> Z[Fim]
    I --> Z
```

---

## 3. Fluxo de Uso de Crédito na Venda

```mermaid
flowchart TD
    A[Iniciar Venda] --> B{Cliente tem crédito?}
    
    B -->|Não| C[Prosseguir sem crédito]
    B -->|Sim| D[Exibir saldo de crédito]
    
    D --> E[Mostrar origem: Indicação, Devolução, etc.]
    E --> F[Mostrar validade]
    
    F --> G{Usar crédito?}
    
    G -->|Usar na Venda Pai| H[Informar valor a usar]
    G -->|Reservar para Entregas| I[Crédito fica disponível nas .E1, .E2...]
    G -->|Não usar agora| C
    
    H --> J{Valor >= Total da venda?}
    J -->|Sim| K[Venda 100% com crédito]
    J -->|Não| L[Crédito + Outra forma de pagamento]
    
    K --> M[Baixa do crédito]
    L --> N[Definir forma complementar]
    N --> M
    
    I --> O[Crédito reservado]
    O --> P[Na entrega .E1]
    
    P --> Q{Usar crédito reservado?}
    Q -->|Sim| R[Abater do valor da entrega]
    Q -->|Não| S[Usar outra forma]
    
    R --> T[Baixa parcial do crédito]
    S --> T
    
    C --> U[Definir forma de pagamento normal]
    M --> V[Venda finalizada]
    T --> V
    U --> V
    
    V --> W[Fim]
```

---

## 4. Fluxo de Devolução de Venda

```mermaid
flowchart TD
    A[Cliente solicita devolução] --> B[Localizar venda original]
    
    B --> C{Dentro do prazo?}
    C -->|Não| D[Devolução negada - Fora do prazo]
    C -->|Sim| E[Selecionar itens a devolver]
    
    E --> F[Informar motivo]
    F --> G[Registrar condição do produto]
    
    G --> H{Precisa aprovação?}
    H -->|Sim| I[Enviar para aprovação]
    H -->|Não| J[Devolução aprovada automaticamente]
    
    I --> K{Aprovado?}
    K -->|Não| L[Devolução negada]
    K -->|Sim| J
    
    J --> M[Gerar NF-e de Entrada - Devolução]
    M --> N[Dar entrada no estoque]
    
    N --> O{Tipo de estorno?}
    O -->|Dinheiro| P[Estornar pagamento]
    O -->|Crédito| Q[Gerar crédito na carteira do cliente]
    O -->|Escolher na hora| R[Perguntar ao cliente]
    
    R --> O
    
    P --> S[Registrar estorno no financeiro]
    Q --> T[Crédito disponível para próximas compras]
    
    S --> U[Devolução concluída]
    T --> U
    D --> V[Fim]
    L --> V
    U --> V
```

---

## 5. Fluxo de Troca de Venda

```mermaid
flowchart TD
    A[Cliente solicita troca] --> B[Localizar venda original]
    
    B --> C{Dentro do prazo?}
    C -->|Não| D[Troca negada - Fora do prazo]
    C -->|Sim| E[Selecionar itens a trocar]
    
    E --> F[Informar motivo]
    F --> G[Selecionar novos produtos]
    
    G --> H[Calcular diferença]
    
    H --> I{Valor da troca?}
    I -->|Novo maior que Antigo| J[Cliente paga diferença]
    I -->|Novo menor que Antigo| K[Cliente recebe crédito ou estorno]
    I -->|Igual| L[Troca sem diferença]
    
    J --> M{Precisa aprovação?}
    K --> M
    L --> M
    
    M -->|Sim| N[Enviar para aprovação]
    M -->|Não| O[Troca aprovada]
    
    N --> P{Aprovado?}
    P -->|Não| Q[Troca negada]
    P -->|Sim| O
    
    O --> R[Gerar NF-e Devolução - Produto antigo]
    R --> S[Entrada no estoque - Produto antigo]
    
    S --> T[Gerar NF-e Venda - Produto novo]
    T --> U[Saída do estoque - Produto novo]
    
    U --> V{Tem diferença a pagar?}
    V -->|Sim| W[Processar pagamento ou crédito]
    V -->|Não| X[Troca concluída]
    
    W --> X
    D --> Y[Fim]
    Q --> Y
    X --> Y
```

---

## 6. Fluxo de Consignação

```mermaid
flowchart TD
    A[Início] --> B[Criar Romaneio de Consignação]
    
    B --> C[Selecionar cliente depositário]
    C --> D[Selecionar produtos e quantidades]
    D --> E[Definir prazo para acerto]
    
    E --> F[Emitir NF-e Remessa em Consignação]
    F --> G[Saída do estoque próprio]
    G --> H[Entrada no estoque em consignação]
    
    H --> I[Consignação ativa]
    
    I --> J{Ação?}
    
    J -->|Acerto parcial| K[Informar itens vendidos pelo cliente]
    J -->|Acerto total| L[Informar todos os itens vendidos ou devolvidos]
    J -->|Devolução total| M[Cliente devolve tudo]
    J -->|Prazo vencendo| N[Alerta automático]
    
    N --> J
    
    K --> O[Separar: Vendidos x A devolver]
    L --> O
    M --> P[Todos os itens voltam]
    
    O --> Q[Gerar NF-e Venda - Itens vendidos]
    Q --> R[Gerar financeiro]
    
    O --> S{Tem itens a devolver?}
    S -->|Sim| T[Gerar NF-e Retorno de Consignação]
    S -->|Não| U[Acerto concluído]
    
    T --> V[Entrada no estoque próprio]
    V --> U
    
    P --> T
    
    R --> U
    
    U --> W{Ainda tem itens em consignação?}
    W -->|Sim| I
    W -->|Não| X[Consignação encerrada]
    
    X --> Y[Fim]
```

---

## 7. Fluxo de Compra Completa

```mermaid
flowchart TD
    A[Início] --> B{Origem?}
    
    B -->|Sugestão automática| C[Sistema sugere reposição]
    B -->|Manual| D[Usuário cria solicitação]
    
    C --> E[Solicitação de Compra]
    D --> E
    
    E --> F{Cotação obrigatória?}
    F -->|Sim| G[Criar cotação]
    F -->|Não| H[Criar pedido direto]
    
    G --> I[Enviar para fornecedores]
    I --> J[Aguardar respostas]
    J --> K[Comparar propostas]
    
    K --> L[Selecionar melhor oferta]
    L --> M[Gerar Pedido de Compra]
    H --> M
    
    M --> N{Valor precisa aprovação?}
    N -->|Sim| O[Enviar para aprovação]
    N -->|Não| P[Pedido aprovado]
    
    O --> Q{Aprovado?}
    Q -->|Não| R[Pedido recusado]
    Q -->|Sim| P
    
    P --> S[Enviar pedido ao fornecedor]
    S --> T[Aguardar entrega]
    
    T --> U[Mercadoria chegou]
    U --> V[Importar NF-e do fornecedor]
    
    V --> W[Conferência física]
    W --> X{Confere com NF?}
    
    X -->|Sim| Y[Entrada no estoque]
    X -->|Divergência| Z[Registrar divergência]
    
    Z --> AA{Tipo de divergência?}
    AA -->|Falta| AB[Reclamar com fornecedor]
    AA -->|Sobra| AC[Devolver ou aceitar]
    AA -->|Avaria| AD[Solicitar troca ou crédito]
    
    AB --> Y
    AC --> Y
    AD --> Y
    
    Y --> AE[Gerar Contas a Pagar]
    AE --> AF[Compra concluída]
    
    R --> AG[Fim]
    AF --> AG
```

---

## 8. Fluxo Financeiro - Recebimento

```mermaid
flowchart TD
    A[Título gerado] --> B[Contas a Receber]
    
    B --> C{Vencimento?}
    C -->|Futuro| D[Aguardar vencimento]
    C -->|Hoje| E[Dia do vencimento]
    C -->|Vencido| F[Título em atraso]
    
    D --> G{Pagamento antecipado?}
    G -->|Sim| H[Baixa com desconto]
    G -->|Não| C
    
    E --> I{Cliente pagou?}
    I -->|Sim| J[Identificar pagamento]
    I -->|Não| F
    
    F --> K[Iniciar régua de cobrança]
    K --> L[Enviar cobrança: Email e WhatsApp]
    
    L --> M{Dias de atraso?}
    M -->|1-7 dias| N[Cobrança amigável]
    M -->|8-30 dias| O[Cobrança firme]
    M -->|31-60 dias| P[Bloquear cliente]
    M -->|Mais de 60 dias| Q[Negativação]
    
    N --> I
    O --> I
    P --> I
    Q --> R{Cliente pagou?}
    
    R -->|Sim| S[Baixar negativação]
    R -->|Não| T[Cobrança judicial]
    
    S --> J
    
    J --> U{Forma de pagamento?}
    U -->|PIX| V[Baixa automática]
    U -->|Boleto| W[Baixa via retorno bancário]
    U -->|Cartão| X[Baixa via conciliadora]
    U -->|Dinheiro| Y[Baixa manual]
    
    V --> Z[Título baixado]
    W --> Z
    X --> Z
    Y --> Z
    
    H --> Z
    
    Z --> AA{Valor correto?}
    AA -->|Sim| AB[Recebimento concluído]
    AA -->|Menor| AC[Baixa parcial - Gerar novo título]
    AA -->|Maior| AD[Gerar crédito para cliente]
    
    AC --> AB
    AD --> AB
    
    T --> AE[Fim]
    AB --> AE
```

---

## 9. Fluxo E-commerce B2B

```mermaid
flowchart TD
    A[Empresa acessa o site] --> B{Tem cadastro?}
    
    B -->|Não| C[Fazer cadastro CNPJ]
    B -->|Sim| D[Fazer login]
    
    C --> E[Preencher dados da empresa]
    E --> F[Enviar para aprovação]
    
    F --> G[Análise de crédito]
    G --> H{Aprovado?}
    
    H -->|Não| I[Cadastro recusado - Notificar]
    H -->|Sim| J[Cadastro aprovado]
    
    J --> K[Definir limite de crédito]
    K --> L[Vincular tabela de preço B2B]
    L --> M[Vincular vendedor]
    
    M --> D
    
    D --> N[Acessar catálogo B2B]
    N --> O[Ver preços de atacado]
    
    O --> P[Adicionar produtos ao carrinho]
    P --> Q{Quantidade mínima?}
    
    Q -->|Não atingiu| R[Alerta: mínimo X unidades]
    Q -->|Atingiu| S[Produto adicionado]
    
    R --> P
    S --> T{Continuar comprando?}
    
    T -->|Sim| P
    T -->|Não| U[Ir para checkout]
    
    U --> V{Pedido mínimo atingido?}
    V -->|Não| W[Alerta: mínimo R$ X]
    V -->|Sim| X[Verificar limite de crédito]
    
    W --> P
    
    X --> Y{Dentro do limite?}
    Y -->|Não| Z[Bloquear - Limite excedido]
    Y -->|Sim| AA[Escolher forma de pagamento]
    
    AA --> AB{Forma?}
    AB -->|Faturado| AC[Prazo 28-35-42 dias]
    AB -->|Boleto| AD[Gerar boleto]
    AB -->|Cartão| AE[Processar cartão]
    AB -->|PIX| AF[Gerar QR Code]
    
    AC --> AG[Pedido gerado]
    AD --> AG
    AE --> AG
    AF --> AG
    
    AG --> AH{Precisa aprovação interna?}
    AH -->|Sim| AI[Enviar para aprovação por alçada]
    AH -->|Não| AJ[Pedido confirmado]
    
    AI --> AK{Aprovado?}
    AK -->|Não| AL[Pedido recusado]
    AK -->|Sim| AJ
    
    AJ --> AM[Notificar cliente]
    AM --> AN[Integrar com ERP]
    AN --> AO[Separação e Entrega]
    
    I --> AP[Fim]
    Z --> AP
    AL --> AP
    AO --> AP
```

---

## 10. Fluxo E-commerce B2C

```mermaid
flowchart TD
    A[Cliente acessa o site] --> B{Tem cadastro?}
    
    B -->|Não| C[Navegar como visitante]
    B -->|Sim| D[Fazer login]
    
    C --> E[Ver catálogo e preços de varejo]
    D --> E
    
    E --> F[Adicionar produtos ao carrinho]
    F --> G{Continuar comprando?}
    
    G -->|Sim| F
    G -->|Não| H[Ir para checkout]
    
    H --> I{Está logado?}
    I -->|Não| J[Cadastro rápido ou login]
    I -->|Sim| K[Confirmar endereço]
    
    J --> K
    
    K --> L[Calcular frete]
    L --> M{Frete grátis?}
    
    M -->|Sim - Atingiu valor| N[Frete R$ 0,00]
    M -->|Não| O[Exibir opções de frete]
    
    N --> P[Escolher forma de pagamento]
    O --> P
    
    P --> Q{Tem crédito de indicação?}
    Q -->|Sim| R[Perguntar se quer usar]
    Q -->|Não| S[Prosseguir]
    
    R --> T{Usar crédito?}
    T -->|Sim| U[Abater do total]
    T -->|Não| S
    
    U --> S
    
    S --> V{Forma de pagamento?}
    V -->|PIX| W[Gerar QR Code]
    V -->|Cartão Crédito| X[Processar pagamento]
    V -->|Boleto| Y[Gerar boleto]
    
    W --> Z{Pagou em 30 min?}
    Z -->|Sim| AA[Pagamento confirmado]
    Z -->|Não| AB[Pedido cancelado]
    
    X --> AC{Aprovado?}
    AC -->|Sim| AA
    AC -->|Não| AD[Pagamento recusado]
    
    Y --> AE[Aguardar pagamento]
    AE --> AF{Pagou em 3 dias?}
    AF -->|Sim| AA
    AF -->|Não| AB
    
    AA --> AG[Pedido confirmado]
    AG --> AH[Enviar email de confirmação]
    AH --> AI[Separação]
    AI --> AJ[Entrega]
    AJ --> AK[Notificar cliente: Entregue!]
    
    AB --> AL[Fim]
    AD --> AL
    AK --> AL
```

---

## 11. Fluxo de Entrega com Rastreamento GPS

```mermaid
flowchart TD
    A[Pedidos prontos para entrega] --> B[Montar romaneio de carga]
    
    B --> C[Roteirização automática]
    C --> D[Atribuir motorista]
    
    D --> E[Motorista abre App]
    E --> F[Ver lista de entregas do dia]
    
    F --> G[Iniciar rota]
    G --> H[GPS ativado - Rastreamento em tempo real]
    
    H --> I[Cliente pode acompanhar no mapa]
    
    I --> J[Motorista chega no endereço]
    J --> K[Check-in automático por GPS]
    
    K --> L[Notificar cliente: Motorista chegou!]
    
    L --> M{Cliente presente?}
    
    M -->|Sim| N[Entregar mercadoria]
    M -->|Não| O[Registrar ocorrência: Ausente]
    
    N --> P[Coletar assinatura digital]
    P --> Q[Tirar foto do comprovante]
    Q --> R[Confirmar entrega no App]
    
    R --> S[Baixa automática no sistema]
    S --> T[Notificar cliente: Entrega realizada!]
    
    O --> U{Reagendar?}
    U -->|Sim| V[Agendar nova tentativa]
    U -->|Não| W[Retornar mercadoria]
    
    V --> X[Próxima entrega da lista]
    W --> X
    T --> X
    
    X --> Y{Mais entregas?}
    Y -->|Sim| J
    Y -->|Não| Z[Finalizar rota]
    
    Z --> AA[Retornar ao CD]
    AA --> AB[Fechar romaneio]
    
    AB --> AC[Fim]
```

---

## 12. Fluxo de Garantia de Produtos

```mermaid
flowchart TD
    A[Cliente abre chamado de garantia] --> B[Informar NF ou nº de série]
    
    B --> C[Sistema localiza produto]
    C --> D{Produto encontrado?}
    
    D -->|Não| E[Solicitar documentação]
    D -->|Sim| F[Verificar prazo de garantia]
    
    E --> F
    
    F --> G{Dentro da garantia?}
    G -->|Não| H[Garantia expirada - Oferecer reparo pago]
    G -->|Sim| I[Garantia válida]
    
    I --> J[Cliente descreve o defeito]
    J --> K[Cliente envia fotos]
    
    K --> L[Criar chamado de garantia]
    L --> M[Enviar para análise técnica]
    
    M --> N[Técnico analisa]
    N --> O{Defeito confirmado?}
    
    O -->|Não| P[Garantia negada - Mau uso]
    O -->|Sim| Q{Tipo de resolução?}
    
    Q -->|Reparo| R[Agendar reparo]
    Q -->|Troca| S[Trocar por produto novo]
    Q -->|Devolução| T[Devolver valor]
    Q -->|Enviar ao fabricante| U[Encaminhar para assistência]
    
    R --> V[Produto reparado]
    S --> W[Gerar NF de troca]
    T --> X[Gerar crédito ou estorno]
    U --> Y[Aguardar retorno do fabricante]
    
    Y --> Z{Fabricante resolveu?}
    Z -->|Sim| AA[Devolver produto ao cliente]
    Z -->|Não| AB[Trocar ou devolver valor]
    
    V --> AC[Entregar ao cliente]
    W --> AC
    X --> AC
    AA --> AC
    AB --> AC
    
    AC --> AD[Fechar chamado]
    
    H --> AE[Fim]
    P --> AE
    AD --> AE
```

---

## Legenda dos Diagramas

| Símbolo | Significado |
|---------|-------------|
| Retângulo arredondado | Início / Fim |
| Retângulo | Processo / Ação |
| Losango | Decisão |
| Seta | Fluxo / Direção |

---

## Próximos Fluxogramas a Criar

- [ ] Fluxo de Produção (PCP)
- [ ] Fluxo de Inventário
- [ ] Fluxo de RH (Admissão)
- [ ] Fluxo de RH (Folha de Pagamento)
- [ ] Fluxo de Contratos
- [ ] Fluxo de Precificação

---

Última atualização: 29/11/2025

PLANAC Distribuidora - ERP - Documentação Oficial
