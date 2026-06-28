# Sistema de Controle de Estoque - Gestão de Dívida Técnica 🛠️

Este repositório contém a entrega do trabalho prático da disciplina de **DIM0501 — Boas Práticas de Programação** (UFRN). 

O objetivo do projeto foi analisar um sistema legado de controle de estoque feito em Python, identificar seus débitos técnicos, priorizá-los e aplicar refatorações para quitar as dívidas mais críticas sem alterar o comportamento esperado do software.

## 👤 Autor
* **Daniel Vítor de Oliveira Bezerra**

## 🎯 Sobre o Projeto original
O sistema é uma aplicação de terminal (*Command Line Interface*) projetada para pequenos comércios. Ele permite:
- Cadastrar produtos (nome, preço e quantidade);
- Registrar vendas (com baixa automática de estoque e cálculo de descontos);
- Listar inventário e emitir relatórios de estoque baixo.

O código original possuía diversas dívidas técnicas acumuladas, incluindo ausência de validações, vazamento de estado em parâmetros mutáveis, números mágicos e forte acoplamento global.

## 🔧 Refatorações Realizadas (Quitação da Dívida)

1. **Robustez na função de vendas (`D2`)**: 
   * **Problema:** O sistema permitia vender quantidades negativas, o que matematicamente injetava produtos fantasmas no estoque.
   * **Solução:** Implementação do padrão *Guard Clauses* para validar a quantidade e o estoque logo no início da função, bloqueando transações inválidas instantaneamente.

2. **Correção de estado compartilhado e nomenclatura (`D1`)**: 
   * **Problema:** A função de adição de produtos sofria do bug clássico do Python de argumento padrão mutável (`hist=[]`), além de usar variáveis não descritivas (`n`, `p`, `q`).
   * **Solução:** Substituição da lista por uma sentinela imutável (`None`) com instanciação local e renomeação de todas as variáveis para refletir a semântica de negócio (`nome`, `preco`, `quantidade`).

## 📄 Relatório Técnico
A análise completa do inventário, matriz de priorização e o *roadmap* detalhado de quitação podem ser encontrados no relatório em PDF anexado neste repositório:
👉 [Acessar Relatório Técnico Completo](./Relatorio_Divida_Tecnica.pdf)