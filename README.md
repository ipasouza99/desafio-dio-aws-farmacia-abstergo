# Desafio DIO — Implementação de Serviços AWS
Abstergo Industries (Hub de Distribuição Farmacêutica — cenário fictício)
Este repositório reúne a documentação do desafio do bootcamp. O trabalho consiste em apresentar uma proposta inicial de adoção de 3 serviços da AWS, priorizando redução de custos e ganho de eficiência na operação.

Observação: este é um desafio documental (análise e proposta). Não exige a implementação dos serviços na AWS.

Empresa (cenário do desafio)
Abstergo Industries — empresa fictícia do setor farmacêutico, atuando como hub de distribuição (B2B): recebe produtos de fabricantes/fornecedores e distribui para redes de farmácias e parceiros.

## Responsável
Ícaro de Souza Passos

## Data
19/02/2026
 ##
Objetivo
Explicar, de forma acessível para um gestor não técnico, como três serviços da AWS podem ajudar a empresa a:

* reduzir custos com infraestrutura e manutenção
 * diminuir trabalho manual em rotinas de TI (backup, expansão de disco, correções)
* melhorar previsibilidade e controle de gastos desde o início
* manter margem para expansão (novos parceiros, novas filiais e, se fizer sentido, B2C no futuro)
##
# Entregáveis
## Relatório principal (proposta completa):
relatorio.md

## Arquitetura (visão simplificada):
arquitetura.md
##
**Serviços AWS abordados**
*  **Amazon S3** — armazenamento de arquivos e documentos (NF-e, PDFs, relatórios etc.)
* **Amazon RDS** — banco de dados gerenciado para pedidos/estoque e dados do sistema
* **AWS Cost Explorer + AWS Budgets** — visibilidade, alertas e limites para controle de gastos
  ##
# Notas
* Para justificar a proposta, o cenário atual foi considerado como on-premises (servidores locais).
* O texto foi escrito pensando em diretoria: pouco jargão e foco no impacto prático.
##
# Referências
* Materiais do Bootcamp DIO + CI&T
* Documentação oficial da AWS (S3, RDS, Cost Explorer e Budgets)
