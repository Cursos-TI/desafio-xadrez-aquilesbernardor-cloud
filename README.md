```c
#include <stdio.h>

// Função recursiva para simular o movimento da Torre (5 casas para a direita)
// Substitui o loop original por recursão. Cada chamada imprime "Direita" e chama a si mesma com steps-1.
// Evita stack overflow limitando a profundidade a 5.
void move_torre(int steps) {
    if (steps <= 0) return;  // Condição base: para a recursão quando steps <= 0
    printf("Direita\n");     // Imprime a direção para uma casa
    move_torre(steps - 1);  // Chamada recursiva para a próxima casa
}

// Função recursiva para simular o movimento do Bispo (5 casas na diagonal cima e direita)
// Usa recursão para os 5 passos. Para cada passo, usa loops aninhados: externo para vertical (Cima),
// interno para horizontal (Direita), imprimindo a combinação "Cima, Direita\n".
// O loop externo controla o componente vertical, o interno o horizontal.
void move_bispo(int steps) {
    if (steps <= 0) return;  // Condição base: para a recursão
    // Loops aninhados para o movimento diagonal de uma casa
    int vertical = 1;    // Componente vertical por passo (1 para cima)
    int horizontal = 1;  // Componente horizontal por passo (1 para direita)
    for (int v = 0; v < vertical; v++) {  // Loop externo: movimento vertical
        printf("Cima");                   // Imprime o componente vertical
        for (int h = 0; h < horizontal; h++) {  // Loop interno: movimento horizontal
            printf(", Direita\n");              // Imprime o componente horizontal com vírgula e quebra de linha
        }
    }
    move_bispo(steps - 1);  // Chamada recursiva para o próximo passo diagonal
}

// Função recursiva para simular o movimento da Rainha (8 casas para a esquerda)
// Substitui o loop original por recursão. Cada chamada imprime "Esquerda" e chama a si mesma com steps-1.
// Evita stack overflow limitando a profundidade a 8.
void move_rainha(int steps) {
    if (steps <= 0) return;  // Condição base: para a recursão
    printf("Esquerda\n");    // Imprime a direção para uma casa
    move_rainha(steps - 1); // Chamada recursiva para a próxima casa
}

// Função para simular o movimento do Cavalo (2 casas para cima e 1 para a direita em "L")
// Usa loops aninhados com múltiplas variáveis e condições. Outer while para fases (vertical/horizontal),
// inner for para movimentos em cada fase. Usa continue e break para controle de fluxo preciso.
// Variáveis: up_count e right_count controlam quantos movimentos em cada direção.
// Phase alterna entre vertical (0) e horizontal (1). Counter total para monitoramento.
void move_cavalo() {
    int up_count = 2;       // Movimentos para cima
    int right_count = 1;    // Movimento para direita
    int phase = 0;          // Fase 0: vertical, Fase 1: horizontal
    int total_steps = up_count + right_count;  // Total de casas percorridas
    int counter = 0;        // Contador de movimentos realizados
    while (phase < 2) {     // Loop externo: processa fases até completar vertical e horizontal
        int moves = (phase == 0) ? up_count : right_count;  // Movimentos na fase atual
        const char* direction = (phase == 0) ? "Cima" : "Direita";  // Direção da fase
        for (int i = 0; i < moves; i++) {  // Loop interno: executa movimentos na fase
            if (counter >= total_steps) {  // Condição de segurança: break se exceder total
                break;
            }
            if (i % 2 == 1 && phase == 0) {  // Condição dummy para demonstrar continue (pula em par)
                continue;
            }
            printf("%s\n", direction);  // Imprime a direção
            counter++;                  // Incrementa contador
        }
        phase++;  // Avança para próxima fase
        if (phase == 2) {  // Break explícito ao final, embora while pare
            break;
        }
    }
}

int main() {
    // Simulação do movimento da Torre
    move_torre(5);
    printf("\n");  // Linha em branco para separar

    // Simulação do movimento do Bispo
    move_bispo(5);
    printf("\n");  // Linha em branco para separar

    // Simulação do movimento da Rainha
    move_rainha(8);
    printf("\n");  // Linha em branco para separar

    // Simulação do movimento do Cavalo
    move_cavalo();

    return 0;
}
```
