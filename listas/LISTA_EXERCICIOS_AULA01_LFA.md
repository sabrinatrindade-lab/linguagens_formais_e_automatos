# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** Murillo Edson de Carvalho Sousa  
**Aluno(a):** Sabrina Borges da Trindade  
**Turma:** ENGCDM3B-MDC078 **Data:** 09/08/2026 

---

## Objetivos

Ao concluir esta lista, você deverá ser capaz de:

- diferenciar sintaxe e semântica;
- reconhecer problemas de escrita, concordância e ordenação;
- classificar erros básicos em trechos de código;
- explicar como o contexto altera o significado;
- distinguir um erro detectado pelo compilador de um erro lógico;
- ordenar as etapas iniciais do processamento realizado por um compilador.

## Orientações

1. Leia cada enunciado com atenção.
2. Não apresente apenas a classificação: escreva uma justificativa curta.
3. Nos exemplos de programação, considere a seguinte pseudolinguagem:
   - `inteiro`, `real` e `lógico` representam tipos;
   - `:=` é o operador de atribuição;
   - variáveis precisam ser declaradas antes do uso;
   - a forma condicional é `se condição então comando`.
4. Quando mais de uma classificação for defensável, indique o critério utilizado.

> **Nota conceitual:** na língua natural, um problema como “vou corre” é mais precisamente um erro gramatical ou de forma verbal. Na análise de compiladores, **erro léxico** possui um sentido técnico: ocorre quando uma sequência de caracteres não pode ser reconhecida como um token válido.

---

## Exercício 1 — Classificação em linguagem natural

Classifique cada sentença utilizando uma das categorias:

- **A — Adequada:** construção sintaticamente adequada no português usual;
- **B — Problema sintático:** problema de ordem, concordância ou estrutura;
- **C — Problema de formação/escrita:** palavra escrita ou flexionada de forma inadequada para o contexto.

| Item | Sentença | Classificação | Justificativa |
|---:|---|:---:|---|
| 1 | “As flores são belas.” | A | construção sintaticamente adequada no português usual  |
| 2 | “As flores é bela.” | B | erro de concordância verbal e nominal com sujeito no plural  |
| 3 | “Vou corre hoje no parque.” | C | verbo "correr" flexionado incorretamente (falta o 'r' de infinitivo). |
| 4 | “Água bebeu José.” | B | Problema de ordem direta dos termos  |
| 5 | “O aluno acabou a prova.” | A | construção sintaticamente adequada no português usual  |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
    A sentença é apenas incomum e menos frequente, tratando-se de um problema de sintaxe (ordem e estrutura dos termos). Apesar da inversão, o contexto permite entender perfeitamente a mensagem, mostrando que a comunicação e a semântica funcionaram (é possível compreender que foi José quem bebeu a água). Além disso, esse tipo de construção pode ser utilizado no sentido conotativo em contextos literários, poemas ou músicas (usando figuras de linguagem como a prosopopeia ou o hiperbato), embora no português usual e na gramática normativa a estrutura seja considerada inadequada.
  
2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**
    As flores são belas
    A flor é bela
    Vou correr hoje no parque
    José bebeu água
    O aluno acabou a prova 
---

## Exercício 2 — Sintaxe e semântica na programação

Analise os trechos abaixo. Classifique o problema predominante como:

- **S — Sintático:** a estrutura não segue a gramática da pseudolinguagem;
- **M — Semântico:** a estrutura pode ser reconhecida, mas seus elementos não são válidos ou compatíveis;
- **V — Válido:** não há erro considerando apenas as regras fornecidas.

> Alguns compiladores podem classificar determinadas situações em fases diferentes. Considere as regras da pseudolinguagem apresentadas no início da lista.

### Item 1

```text
45 := a;
```

Classificação: S 

Justificativa:  
A regra de atribuição exige que o lado esquerdo seja uma variável.O numeral 
45 é uma contante e não pode receber atribuição de valor .  A forma correta seria a := 45; . 
### Item 2

```text
então (a < 10) se;
```

Classificação: S 

Justificativa:  
A estrutura condicional está invertida. O correto seria se (a<10) então;
____________________________________________________________________________

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: M 

Justificativa:  
estrutura da instrução está sintaticamente correta (tipo identificador; e variável := valor;). O erro é de incompatibilidade de tipos (semântica): a variável foi declarada como inteiro, mas tentou-se atribuir um valor decimal/ponto flutuante (4.5).
### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: M 

Justificativa:  
sintaxe da atribuição (variável := valor;) está correta. Porém, ocorre um erro semântico de variável não declarada (o compilador não conhece o tipo nem a existência de media na tabela de símbolos antes de seu uso).
### Item 5

```text
real media;
media := 10.0;
```

Classificação: V 

Justificativa:  
A variável media foi declarada corretamente com o tipo real (equivalente ao float) e recebe um valor decimal compatível (10.0). 
A sintaxe e a semântica estão perfeitas.

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: V 

Justificativa:  
A estrutura condicional (se ... então) e a instrução de atribuição seguem a gramática da pseudolinguagem. Como a é inteira, a comparação < 10 e a soma a + 1 são operações válidas.
---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
​Na frase 1 ("Eu caminho todos os dias."): A palavra é um verbo (verbo caminhar na 1ª pessoa do singular do presente). Significa a ação de andar ou locomover-se a pé.
​Na frase 2 ("O caminho é longo."): A palavra é um substantivo masculino (acompanhado pelo artigo "O"). Significa um trajeto, via, estrada ou percurso.
​(O contexto do pronome "Eu" versus

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
Na frase 1 ("Vou colher flores."): A palavra é um verbo no infinitivo (formando locução verbal com "Vou"). Significa a ação de apanhar, apanhar plantas ou colher frutos/flores.
​Na frase 2 ("A colher caiu no chão."): A palavra é um substantivo feminino (acompanhado pelo artigo "A"). Significa o utensílio de cozinha/talher usado para alimentação.

### Caso C — programação

Observe os trechos:

```text
inteiro soma;
soma := 10;
```

```text
função soma(inteiro a, inteiro b)
    retorne a + b;
fim
```

1. O que o nome `soma` representa em cada trecho?
2. Que informações o compilador precisa consultar para interpretar corretamente esse nome?

**Resposta:**  
1. No primeiro trecho, `soma` representa uma variável simples destinada a guardar um valor inteiro. No segundo trecho, `soma` representa o identificador de uma função que executa uma operação e retorna um resultado.

2. O compilador consulta a Tabela de Símbolos para verificar a categoria do identificador (se é variável ou função), o escopo da declaração, o tipo de dado e a estrutura sintática na qual ele é chamado (presença de parênteses/parâmetros vs. atribuição direta).
  
### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
O compilador precisa considerar esses três fatores na Análise Semântica para garantir a integridade do programa:

1. **Declarações:** Verificam se os identificadores utilizados existem no programa, evitando acessos a referências inexistentes.
2. **Tipos:** Garantem a compatibilidade das operações e atribuições, impedindo erros de execução por manipulação inadequada de dados na memória.
3. **Escopos:** Definem a visibilidade e o tempo de vida das variáveis, permitindo que o compilador resolva ambiguidades de nomes e garanta que cada recurso só seja acessado onde é permitido.
  
---

## Exercício 4 — Validade e erros lógicos

Um aluno desenvolveu um programa para conceder **10% de aumento** ao salário de um funcionário. O código deveria multiplicar o salário por `1.1`, mas foi escrito assim:

```text
real salario;
real novoSalario;

novoSalario := salario * 11;
```

O programa é aceito pelo compilador e executado normalmente.

Responda:

1. O trecho está sintaticamente correto? Justifique.

   **Resposta:**  
Sim, o trecho está sintaticamente correto. Todas as instruções seguem rigorosamente as regras gramaticais da linguagem: declarações com tipo e identificador terminadas em ponto e vírgula (`real salario;`), e atribuição com operador válido (`:=`) e expressão matemática bem-formada (`salario * 11;`).
2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
   Não. Ambas as variáveis (`salario` e `novoSalario`) foram devidamente declaradas antes do uso. Além disso, não há incompatibilidade de tipos, pois a operação de multiplicação é válida e o resultado é compatível com a variável `novoSalario` (do tipo `real`). O erro presente no código é estritamente um erro de lógica (regra de negócio), e não de compilação.
   
4. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
   Não. O objetivo era conceder um aumento de 10% (o que corresponderia a multiplicar por 1.10 ou somar salario * 0.10). Ao multiplicar por 11, o programa calcula 1100% do salário (um aumento de 1000%), entregando um resultado incorreto para a regra de negócio esperada.

5. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
  Trata-se de um **erro lógico** (ou de regra de negócio). O código é válido sintaticamente e semanticamente para o compilador, mas a fórmula matemática utilizada não reflete a intenção do programa.
6. Corrija a linha responsável pelo problema.

```text
novoSalario := salario * 1.10;

```

---

## Exercício 5 — Ordem de processamento

Organize as etapas abaixo na ordem didática mais comum de um compilador:

- análise semântica;
- análise léxica (*scanner*);
- análise sintática (*parser*).

### Parte A — Lista numerada

1.  Análise léxica (*scanner*);
2. Análise sintática (*parser*).
3. análise semântica; 

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica | A sequência de caracteres do código-fonte para transformá-los em tokens. | Caractere inválido ou símbolo desconhecido no código (ex: `@` ou `2abc`). |
| Análise sintática | A sequência de tokens para verificar se respeita a estrutura da gramática. | Comando fora de ordem ou faltando estrutura (ex: `45 := a;` ou falta de parênteses). |
| Análise semântica | O significado do código, a coerência dos tipos de dados e os escopos. | Incompatibilidade de tipos (ex: atribuir `4.5` a um `inteiro`) ou variável não declarada. |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte -> [Análise Léxica] -> tokens -> [Análise Sintática] -> estrutura sintática
             -> [Análise Semântica] -> código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
A análise semântica depende das etapas anteriores porque precisa que o código já esteja estruturado e sem erros gramaticais para poder analisar seu significado. Primeiro, a análise léxica transforma o código-fonte em tokens válidos; depois, a análise sintática organiza esses tokens em uma árvore sintática bem-formada. Somente com essa estrutura definida é que o compilador consegue checar se os tipos, escopos e declarações fazem sentido na lógica do programa.
---

## Desafio opcional — Crie seus próprios exemplos

Crie três pequenos exemplos:

1. uma frase ou código com problema de escrita/tokenização;
2. uma construção com erro sintático;
3. um programa sintaticamente válido, mas com erro lógico.

Para cada exemplo, apresente a classificação e a justificativa.

---

## Síntese

Complete:

- **Léxico** está relacionado à validade dos caracteres e à formação dos tokens (palavras reservadas, símbolos e identificadores).
- **Sintaxe** está relacionada à estrutura gramatical e à ordem correta das instruções segundo as regras da linguagem.
- **Semântica** está relacionada ao significado do código, como a coerência dos tipos de dados, escopos e declarações.
- **Erro lógico** ocorre quando o programa compila e roda sem erros, mas gera um resultado incorreto para o objetivo pretendido.

