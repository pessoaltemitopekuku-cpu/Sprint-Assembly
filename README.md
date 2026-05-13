# Soluções em Código de Baixo Nível

## Integrantes

- Carlos Eduardo Affonso — RM 569676
- Gabriel Oliveira Gusmão Florencio dos Santos — RM 573747
- Gabrieli de Lima Pettena de Oliveira — RM 569799
- Igor Massone Monteiro — RM 573853
- Murilo Massahiro Kamei de Santi — RM 573046
- Temitope Kuku da Silva Ogunbanjo — RM 573772

---

# Problema

Eletropostos realizam constantemente operações simples, como monitoramento de bateria e controle de carregamento. Muitas vezes, essas tarefas são executadas utilizando sistemas com alto nível de abstração, aumentando o consumo computacional e energético.

Mesmo pequenas ineficiências podem gerar desperdício quando aplicadas em larga escala.

---

# Justificativa

A eficiência computacional também influencia no consumo energético. Quanto maior o número de instruções executadas pelo processador, maior é o uso de recursos da máquina.

Utilizando programação em baixo nível, é possível reduzir operações desnecessárias e ter maior controle sobre o funcionamento do processador.

---

# Proposta de Solução

O projeto propõe uma simulação simples de controle de carregamento utilizando Assembly x86.

O sistema:

- Verifica a carga atual da bateria
- Compara com a capacidade máxima
- Decide se o carregamento deve continuar
- Informa quando a bateria está totalmente carregada

A proposta demonstra como instruções de baixo nível podem reduzir overhead computacional.

---

# Arquitetura Utilizada

- Assembly NASM
- Arquitetura x86
- Registradores da CPU
- Syscalls Linux
- Manipulação direta de memória

---

# Código Assembly

```asm
section .data
    ; Capacidade máxima da bateria (44.9 kW -> 449)
    batteryMax dd 449

    ; Carga atual da bateria (44.8 kW -> 448)
    currentPower dd 448

    ; Mensagem de carregamento
    charging db "Charging...", 10
    chargingLen equ $-charging

    ; Mensagem de bateria cheia
    full db "Battery Full", 10
    fullLen equ $-full

section .text
    global _start

_start:

    ; Carregar valores
   
    ; eax = currentPower
    mov eax, [currentPower]

    ; ebx = batteryMax
    mov ebx, [batteryMax]

    ; Comparar valores da bateria

    ; compara eax com ebx
    cmp eax, ebx

    ; Se eax < ebx -> executa charge
    jl charge

    ; Bateria cheia
    ; Mensagem que é printada quando a bateria já corresponde ao valor máximo

    ; syscall write
    mov eax, 4
    mov ebx, 1
    mov ecx, full
    mov edx, fullLen
    int 0x80

    ; pula para exit
    jmp exit

charge:

    ; Executado quando há possibilidade de carregar a bateria do carro 
   
    ; Mostrar "Charging..."
    ; syscall write
    mov eax, 4
    mov ebx, 1
    mov ecx, charging
    mov edx, chargingLen
    int 0x80

    ; Simular bateria cheia
    ; Armazenar o valor máximo da bateria no valor atual
    
    ; eax = batteryMax
    mov eax, [batteryMax]

    ; currentPower = eax
    mov [currentPower], eax

exit:

    ; Encerrar o programa

    ; syscall exit
    mov eax, 1
    xor ebx, ebx
    int 0x80
```

---

# Impactos Esperados

- Redução de processamento desnecessário
- Melhor aproveitamento de recursos computacionais
- Menor consumo energético em sistemas embarcados
- Maior eficiência operacional em eletropostos

---

# Relação com Sustentabilidade e Energias Renováveis

O projeto demonstra que otimizações computacionais também contribuem para sustentabilidade.

Ao reduzir consumo de CPU e desperdício computacional, sistemas de carregamento elétrico podem operar de forma mais eficiente, auxiliando no uso consciente de energia e na melhoria da infraestrutura ligada à mobilidade elétrica.
