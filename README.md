README — Soluções em Código de Baixo Nível
Título do Projeto
Soluções em Código de Baixo Nível
Integrantes
Carlos Eduardo Affonso — RM 569676
Gabriel Oliveira Gusmão Florencio dos Santos — RM 573747
Gabrieli de Lima Pettena de Oliveira — RM 569799
Igor Massone Monteiro — RM 573853
Murilo Massahiro Kamei de Santi — RM 573046
Temitope Kuku da Silva Ogunbanjo — RM 573772
Problema

Eletropostos realizam constantemente operações simples, como monitoramento de bateria e controle de carregamento. Muitas vezes, essas tarefas são executadas utilizando sistemas com alto nível de abstração, aumentando o consumo computacional e energético.

Mesmo pequenas ineficiências podem gerar desperdício quando aplicadas em larga escala.

Justificativa

A eficiência computacional também influencia no consumo energético. Quanto maior o número de instruções executadas pelo processador, maior é o uso de recursos da máquina.

Utilizando programação em baixo nível, é possível reduzir operações desnecessárias e ter maior controle sobre o funcionamento do processador.

Proposta de Solução

O projeto propõe uma simulação simples de controle de carregamento utilizando Assembly x86.

O sistema:

Verifica a carga atual da bateria
Compara com a capacidade máxima
Decide se o carregamento deve continuar
Informa quando a bateria está totalmente carregada

A proposta demonstra como instruções de baixo nível podem reduzir overhead computacional.

Arquitetura Utilizada
Assembly NASM
Arquitetura x86
Registradores da CPU
Syscalls Linux
Manipulação direta de memória
