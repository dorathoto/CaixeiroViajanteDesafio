
# Desafio Caixeiro Viajante

### Porque esse desafio?

**Fácil de entender, difícil de resolver:** O problema em si é muito simples de explicar: encontrar a rota mais curta que visite todas as cidades uma única vez e retorne à cidade de origem. No entanto, encontrar a solução ótima é extremamente complexo à medida que o número de cidades aumenta. Essa combinação de simplicidade conceitual e dificuldade computacional o torna atraente para programadores e pesquisadores.

-   **Aplicações práticas:** O problema do caixeiro viajante tem inúmeras aplicações no mundo real, como logística e planejamento de rotas de transporte, otimização de circuitos em placas eletrônicas, sequenciamento de DNA e até mesmo planejamento de missões espaciais. 
    
-   **Referência em Ciência da Computação:** O problema é **um dos mais estudados** na área de otimização combinatória e teoria da complexidade. Ele é classificado como **NP-difícil**, o que significa que não existe um algoritmo conhecido que possa resolvê-lo de forma eficiente para um grande número de cidades. Isso o torna um desafio clássico para testar e desenvolver novas técnicas algorítmicas.

## Quais algoritmos podemos usar para resolver?
- **Força bruta (Busca exaustiva)**: Testa todas as permutações possíveis das cidades e escolhe a de menor custo.
- **Branch and Bound:** Utiliza uma estratégia de busca inteligente para eliminar ramos da árvore de busca que não podem levar a soluções melhores que a atual. É mais eficiente que a força bruta, mas ainda pode ser lento para instâncias grandes.
- **Heurísticas Construtivas:** Constroem uma solução passo a passo, tomando decisões "gulosas" em cada etapa. Exemplos: Algoritmo do Vizinho Mais Próximo :), Inserção Mais Barata, Savings, etc.
-  **Heurísticas de Melhoria:** Partem de uma solução inicial e tentam melhorá-la iterativamente através de trocas ou movimentos. Exemplos: 2-opt, 3-opt, Lin-Kernighan.
-   **Metaheurísticas:** Estratégias de busca mais sofisticadas que exploram o espaço de soluções de forma inteligente, guiadas por mecanismos de busca inspirados na natureza ou em outros processos. Ex: Algoritmos Genéticos :|, Simulated Annealing, Colônia de Formigas, Busca Tabu.
-  **Redes Neurais:** Podem ser treinadas para aprender a resolver o problema, mas geralmente não garantem a otimalidade e podem ser difíceis de interpretar. Mas é divertido de programar :)
-   **Algoritmos Híbridos:** Combinam diferentes técnicas para obter melhores resultados.
- E mais algumas que não faço nem idéia, o céu é o limite.

## Nosso desafio
Linguagem recomendada: C#
Para facilitar vamos fazer só com 3 cidades :)

|Distância| 0. Atibaia | 1. Piracaia | 2. Bragança Paulista |
|------ | ------ | ------ |------ |
|0. Atibaia |	0	|	33	|	25	|
|1. Piracaia|	33	|	0	|	35	|
|2. Bragança Paulista|	25	|	35	|	0	|

**Objetivo é calcular qual o melhor trajeto? ex:**

    Atibaia -> Piracaia -> Bragança -> Atibaia

*(aqui vamos pela dom pedro para piracaia e de Piracaia a Bragança vai por Rod. Aldo Bolini e volta de Bragança para Atibaia pela Fernão dias)*

Ou

    Atibaia -> Bragança -> Piracaia -> Atibaia

*(Aqui vamos pela fernão Dias até Bragança, depois pela Aldo Bolini até Piracaia e voltamos pra Atibaia pela Dom Pedro)*

**Minha Sugestão:**
Converter essas distâncias em uma Matriz

    		int[,] distancias = {
					{ 0, 10, 15 }, 
					{ 10, 0, 20 }, 
					{ 15, 20, 0 }  
				};

Uma possibilidade via força bruta:

    using System;
    
    class Program {
        static void Main() {
            int[,] distancias = {
                { 0, 10, 15 }, 
                { 10, 0, 20 }, 
                { 15, 20, 0 }  
            };
    
            int custoRota1 = distancias[0, 1] + distancias[1, 2] + distancias[2, 0]; // 0 -> 1 -> 2 -> 0
            int custoRota2 = distancias[0, 2] + distancias[2, 1] + distancias[1, 0]; // 0 -> 2 -> 1 -> 0
    
            if (custoRota1 < custoRota2) {
                Console.WriteLine("Rota mais curta 1: 0 -> 1 -> 2 -> 0 - custo:"  + custoRota1);
            } else {
                Console.WriteLine("Rota mais curta 2: 0 -> 2 -> 1 -> 0 - custo:"  + custoRota2);
            }
        }
    }

Vamos melhorar o código acima? faça outras opções de algoritmo ou leve ao extremo, faça com 4 cidades.

