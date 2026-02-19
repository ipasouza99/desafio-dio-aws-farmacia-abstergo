# Arquitetura Proposta — Abstergo Industries (Hub de Distribuição Farmacêutica B2B)

Este documento apresenta uma **visão simplificada** da arquitetura proposta para a Abstergo Industries (cenário fictício), usando **três serviços AWS** com foco em **economia**, **simplicidade operacional** e **base para crescimento**.

Serviços considerados:
- Amazon S3
- Amazon RDS
- AWS Cost Explorer + AWS Budgets

---

## Visão geral (o que fica onde)

A proposta separa a solução em três partes fáceis de entender:

1. **Dados do sistema (pedidos/estoque/cadastros)** → ficam em um banco gerenciado no **Amazon RDS**  
2. **Arquivos e documentos (NF-e, PDFs, relatórios, anexos)** → ficam no **Amazon S3**  
3. **Acompanhamento e limite de gastos** → fica no **Cost Explorer + Budgets** (painéis e alertas)

Importante: o Cost Explorer/Budgets serve para **gestão de custos**. Ele não executa tarefas da aplicação (como e-mail ou atualização de estoque).

---

## Componentes

### Amazon S3 — Arquivos e documentos da operação

Uso típico na Abstergo:
- armazenar **XML/PDF de notas fiscais**, comprovantes e relatórios
- guardar documentos internos e anexos de processos
- organizar por pastas lógicas (ex.: ano/mês/parceiro) para facilitar auditoria

Por que ajuda a reduzir custo:
- paga-se **pelo volume usado**, sem precisar comprar storage “sobrando”
- elimina manutenção de servidor/NAS de arquivos
- permite arquivar conteúdo antigo com regras simples (lifecycle), quando aplicável

---

### Amazon RDS — Banco de dados do sistema

Uso típico na Abstergo:
- armazenar dados do sistema de **pedidos, estoque, produtos, clientes/parceiros e registros de integração**
- manter backups e rotinas básicas de manutenção de forma gerenciada

Por que ajuda a reduzir custo e risco:
- diminui o trabalho com atualização/backup do banco local
- reduz indisponibilidade causada por falhas comuns de infraestrutura
- facilita crescimento gradual sem “troca de servidor” toda hora

---

### AWS Cost Explorer + AWS Budgets — Visibilidade e controle de gastos

Uso típico na Abstergo:
- visualizar gastos por serviço e por período no **Cost Explorer**
- criar **orçamentos** e alertas (e-mail) no **Budgets**
- separar custos por projeto/ambiente usando **tags** (ex.: Projeto=Abstergo, Ambiente=Prod)

Por que isso é importante:
- evita surpresas na fatura
- ajuda a identificar consumo fora do padrão logo no início

---

## Fluxo simplificado

### Operação 
1. O sistema registra dados de pedidos e estoque no **Amazon RDS**
2. Documentos e anexos (NF-e, PDFs, relatórios) são armazenados no **Amazon S3**
3. As equipes consultam essas informações conforme permissões e necessidade

### Gestão (controle financeiro)
1. TI/Financeiro acompanha o consumo no **Cost Explorer**
2. O **Budgets** envia alertas quando o gasto se aproxima do limite definido

---

## Impacto esperado em custos

- menos gasto recorrente com servidor físico, energia e manutenção
- redução de trabalho manual (backup, expansão de disco, correções emergenciais)
- melhor previsibilidade, com alertas e acompanhamento de gastos

---

## Considerações finais

Esta arquitetura é uma proposta inicial para orientar a decisão do desafio. Em um cenário real, os próximos passos seriam:
- confirmar volume de dados e arquivos (tamanho, crescimento e retenção)
- definir motor do banco (ex.: MySQL/PostgreSQL) e nível de disponibilidade necessário
- estimar custo mensal inicial e planejar uma migração por fases

## Evolução 
A base em nuvem facilita expandir o modelo **B2B** (mais parceiros/filiais) e, se desejado no futuro, abrir um canal **B2C** sem recomeçar do zero.
