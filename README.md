# Mini-MIPS 8-bits — Simulador Monociclo

Simulador em C de um processador **Mini-MIPS de 8 bits** com arquitetura **monociclo**, desenvolvido para a disciplina de Projeto Integrador II do curso de Engenharia da Computação da UNIPAMPA.

> Parte de uma série de três implementações do Mini-MIPS:
> 1. **Monociclo — você está aqui**
> 2. [Multiciclo](https://github.com/Leonardo-Gonfre/mini-mips-multiciclo)
> 3. [Pipeline](https://github.com/Leonardo-Gonfre/Mini-Mips-Pipeline)

---

## O que é a arquitetura Monociclo?

Na arquitetura **monociclo**, cada instrução é executada em **um único ciclo de clock** — o ciclo dura o tempo necessário para a instrução mais lenta. É a implementação mais simples do processador MIPS, servindo como base para entender as evoluções multiciclo e pipeline.

---

## Funcionalidades

| Opção | Descrição |
|-------|-----------|
| Carregar memória de instruções | Lê arquivo `.mem` com as instruções em binário |
| Carregar memória de dados | Lê arquivo `.dat` com os dados iniciais |
| Imprimir memórias | Exibe instruções e dados carregados |
| Imprimir registradores | Exibe o banco de 8 registradores |
| Imprimir simulador completo | Exibe todo o estado da CPU |
| Salvar `.asm` | Exporta o programa em Assembly |
| Salvar `.dat` | Exporta a memória de dados |
| Executar programa (Run) | Roda todas as instruções |
| Executar uma instrução (Step) | Executa instrução por instrução |
| Voltar uma instrução (Back) | Desfaz a última instrução |

---

## Estrutura de dados

```c
// Memória de instruções separada da memória de dados
memoria_instrucao { instrucao *inst, tamanho }
memoria_dados     { int *dados, tamanho }

// Banco de registradores
banco_registradores { char reg[8] }

// Instrução decodificada
instrucao { tipo, bin[17], opcode, rs, rt, rd, funct, imm, addr }
```

### Tipos de Instrução suportados

- **Tipo R:** `add`, `sub`, `and`, `or`
- **Tipo I:** `addi`, `lw`, `sw`, `beq`
- **Tipo J:** `jump`

---

## Como compilar e executar

```bash
gcc -o main main.c
./main
```

### Formato dos arquivos de entrada

**`.mem`** — instruções em binário (16 bits por linha):
```
0000000100100011
1010000000000101
```

**`.dat`** — dados em decimal (um por linha):
```
10
25
0
```

---

## Evolução da série Mini-MIPS

| Versão | Ciclos/instrução | Diferencial |
|--------|-----------------|-------------|
| **Monociclo** | 1 (fixo) | Mais simples, ciclo = instrução mais lenta |
| [Multiciclo](https://github.com/Leonardo-Gonfre/mini-mips-multiciclo) | 3–5 (variável) | FSM com 11 estados, back-step, estatísticas |
| [Pipeline](https://github.com/Leonardo-Gonfre/Mini-Mips-Pipeline) | ~1 (paralelo) | 5 estágios, forwarding, detecção de hazards |

---

## Tecnologias

- **Linguagem:** C (C99)
- **Compilador:** GCC

---

## Autor

**Leonardo Gonçalves de Freitas**
Estudante de Engenharia da Computação — UNIPAMPA
[LinkedIn](https://linkedin.com/in/leonardogoncalvesfreitas) · [GitHub](https://github.com/Leonardo-Gonfre)