# Sistema de Controle de Frequência

> **EN:** Command-line attendance tracker written in C. It records a student's absences per course, calculates the attendance rate and the 25% absence limit, and saves every report to a text file, adding new absences to previous records.

Programa em C, para o terminal, que controla as faltas de alunos por matéria. Ele calcula a frequência, mostra o limite de faltas permitido (25% das aulas) e avisa quantas aulas o aluno ainda pode faltar. Cada consulta fica salva em `relatorio.txt`, e, se o aluno já tiver registro na matéria, as faltas novas são somadas às anteriores.

Projeto feito no 1º semestre de Ciência da Computação (Unisantos).

## Funcionalidades

- Escolha do curso (Ciência da Computação ou Sistemas de Informação) e do aluno, com opção de digitar outro nome
- Cinco matérias, cada uma com a sua carga de aulas (Humanismo tem 40 aulas; as demais, 80)
- Cálculo da **frequência** e do **limite de faltas** (25% do total de aulas)
- Aviso de quantas aulas ainda podem ser faltadas, ou de que o limite foi atingido ou ultrapassado
- **Histórico em arquivo:** lê o `relatorio.txt` para achar registros anteriores e acrescenta as faltas novas
- Validação das entradas: opção inexistente, texto no lugar de número e número de faltas negativo

## Como compilar e rodar

```bash
gcc -Wall -Wextra -o frequencia main.c
./frequencia
```

No Windows: `frequencia.exe`.

## Exemplo de uso

```
===== CURSOS =====
1 - Ciencia da Computacao
2 - Sistemas de Informacao

Escolha um curso: 1
Escolha o aluno: 1
Escolha a materia: 5
Digite o numero de faltas: 6

===== RELATORIO =====
Aluno: Eloah
Materia: Algoritmos
Total de aulas: 80
Faltas: 6
Frequencia: 92%
Limite de faltas: 20
Ainda pode faltar 14 aulas.

Relatorio salvo em relatorio.txt
```

Rodando de novo para o mesmo aluno e a mesma matéria, o programa encontra o registro anterior:

```
Aluno ja possui registro nesta materia.
Faltas atuais: 6
Quantas faltas deseja adicionar? 3
...
Faltas: 9
Frequencia: 88%
Ainda pode faltar 11 aulas.
```

## Como funciona

1. O programa lê o curso, o aluno e a matéria. A matéria define o total de aulas.
2. Abre o `relatorio.txt` (se existir) e procura a última quantidade de faltas daquele aluno naquela matéria.
3. Se achar, pergunta quantas faltas adicionar; se não, pergunta o total de faltas.
4. Calcula:
   - limite de faltas = 25% do total de aulas
   - frequência = (aulas − faltas) × 100 ÷ aulas
   - aulas que ainda pode faltar = limite − faltas
5. Mostra o relatório na tela e o acrescenta ao final do `relatorio.txt`.

## Tecnologias

- Linguagem C
- Leitura e escrita de arquivos (`fopen`, `fgets`, `sscanf`, `fprintf`)
