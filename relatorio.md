# RELATÓRIO DE IMPLEMENTAÇÃO DE SERVIÇOS AWS
## Abstergo Industries — Hub de Distribuição Farmacêutica

**Data:** 19/02/2026  
**Empresa:** Abstergo Industries  
**Responsável:** Ícaro de Souza Passos  

---

## Introdução

Este relatório apresenta uma proposta inicial para a Abstergo Industries adotar **três serviços da AWS**, priorizando **redução de custos** e **simplificação operacional**.

A Abstergo (cenário fictício) atua como **hub de distribuição farmacêutica (B2B)**: recebe produtos de fabricantes/fornecedores, consolida estoque e pedidos e distribui para redes de farmácias e empresas parceiras. Esse tipo de operação depende de sistemas estáveis para **pedidos, estoque, documentos fiscais** e **integrações B2B**.

Além do cenário atual, a nuvem também ajuda na **flexibilidade para expansão**: crescimento por regiões/filiais, entrada de novos parceiros e, se fizer sentido no futuro, a possibilidade de criar um canal **B2C (venda direta ao cliente final)** sem recomeçar do zero.

**Nota:** este desafio é documental (análise e proposta)

---

## Cenário atual

Como ponto de partida, considera-se que a Abstergo opera hoje “no local” (on-premises), com:

- servidores locais para sistema e banco de dados (pedidos/estoque)
- armazenamento interno para documentos (NF-e, PDFs, relatórios)
- rotinas de backup manuais ou pouco automatizadas
- custos recorrentes de manutenção, energia, troca de peças e suporte

Na prática, esse modelo costuma trazer alguns impactos:
- compra de servidor “para o pico” (custo alto e ociosidade em períodos de baixa)
- crescimento contínuo de arquivos e backups (mais disco + mais trabalho)
- risco de indisponibilidade por falha de hardware e pouca redundância
- equipe de TI gastando tempo com infraestrutura em vez de melhorias do sistema

---

## Proposta

A proposta foi organizada em três frentes, cada uma atacando um ponto comum do cenário on-premises: **arquivos**, **banco de dados** e **controle de gastos**.

---

### 1) Amazon S3 — Arquivos e documentos (baixo custo e escalável)

**Onde entra:** armazenamento de documentos e arquivos operacionais.

**Aplicação na Abstergo:**
- guardar **XML/PDF de notas fiscais**, relatórios e documentos internos
- substituir NAS/servidor de arquivos e reduzir a necessidade de expansão de disco
- organizar por pastas lógicas (ex.: ano/mês/parceiro) para facilitar auditoria e recuperação

**Resultado esperado:**
- menos compra de storage e menos manutenção local
- paga-se **pelo que realmente usa**, com crescimento automático conforme a demanda

---

### 2) Amazon RDS — Banco de dados gerenciado (menos manutenção)

**Onde entra:** banco de dados do sistema de pedidos/estoque.

**Aplicação na Abstergo:**
- hospedar o banco do sistema (clientes/parceiros, produtos, pedidos e registros da operação)
- reduzir tarefas repetitivas de administração (backup, atualizações e manutenção básica)
- aumentar confiabilidade, diminuindo paradas por problemas comuns de infraestrutura local

**Resultado esperado:**
- menos tempo “apagando incêndio” com banco local
- backups e rotinas básicas ficam mais previsíveis, com menor esforço operacional

---

### 3) AWS Cost Explorer + AWS Budgets — Controle e previsibilidade de gastos

**Onde entra:** gestão financeira da conta AWS (visibilidade e alertas).

**Aplicação na Abstergo:**
- acompanhar, em painel, **onde o dinheiro está sendo gasto** (por serviço e por período)
- criar **orçamentos por área** e receber alertas quando atingir limites definidos
- identificar rapidamente “gastos fora do esperado” e agir antes de virar problema
- usar tags (ex.: `Projeto=Abstergo`, `Ambiente=Prod/Homolog`) para separar custos por projeto/time

**Resultado esperado:**
- previsibilidade para o financeiro e menos surpresa no fim do mês
- redução de desperdício por recurso esquecido/ligado sem necessidade

---

## Conclusão

A combinação proposta é simples, mas cobre três necessidades típicas do cenário on-premises e já traz ganhos práticos:

- **Amazon S3**: armazenamento de documentos e arquivos operacionais com custo sob demanda  
- **Amazon RDS**: banco de dados gerenciado, com menos manutenção e maior confiabilidade  
- **Cost Explorer + Budgets**: acompanhamento e controle de custos desde o início do uso da AWS  

### Flexibilidade para expansão

Além da economia, a base em nuvem facilita evoluir a operação por etapas:
- integrar novos parceiros e abrir novas filiais/centros de distribuição com menos esforço
- lidar melhor com picos de demanda sem compra de servidor
- manter caminho aberto para um eventual canal **B2C**, se isso fizer sentido no futuro

---

## Arquivos complementares

- `arquitetura.md` (visão simplificada da solução)

---

**Assinatura do Responsável pelo Projeto:**  
Ícaro de Souza Passos
