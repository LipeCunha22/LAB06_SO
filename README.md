# LAB06_SO
# LAB 06 - Memória. referente ao aluno Luis Felipe Cunha - 04P11
# RA: 10419514

# 1.Considerando a estrutura de dados celula, crie três instâncias do objeto célula (três valores na lista); 
#include <stdio.h>
#include <stdlib.h>

struct reg {
    int conteudo;              // Valor armazenado na célula
    struct reg *prox;          // Ponteiro para a próxima célula
};

typedef struct reg celula;     // Define "celula" como um alias para "struct reg"

int main() {
    // Criando as três células da lista encadeada dinamicamente
    celula *primeira = (celula *)malloc(sizeof(celula));
    celula *segunda = (celula *)malloc(sizeof(celula));
    celula *terceira = (celula *)malloc(sizeof(celula));

    // Verificando se a alocação de memória foi bem-sucedida
    if (primeira == NULL || segunda == NULL || terceira == NULL) {
        printf("Erro ao alocar memória.\n");
        return 1;
    }

    // Atribuindo valores às células
    primeira->conteudo = 10;
    primeira->prox = segunda;    // Conecta a primeira célula à segunda

    segunda->conteudo = 20;
    segunda->prox = terceira;    // Conecta a segunda célula à terceira

    terceira->conteudo = 30;
    terceira->prox = NULL;       // A última célula aponta para NULL, indicando o final da lista

    // Percorrendo a lista e imprimindo os valores
    celula *p = primeira;
    while (p != NULL) {
        printf("Valor: %d\n", p->conteudo);
        p = p->prox;             // Avança para a próxima célula
    }

    // Liberando a memória alocada
    free(primeira);
    free(segunda);
    free(terceira);

    return 0;
}

# 2. Construa uma função que imprima todos os valores da lista; 
#include <stdio.h>
#include <stdlib.h>

struct reg {
    int conteudo;
    struct reg *prox;
};

typedef struct reg celula;

//Função para imprimir todos os valores da lista encadeada!!
void imprimeLista(celula *inicio) {
    celula *p = inicio;  //ponteiro para percorrer a lista

    while (p != NULL) {  //Percorre até encontrar NULL (fim da lista)
        printf("Valor: %d\n", p->conteudo);
        p = p->prox;     //Avança para a próxima célula
    }
}

int main() {
    //Criação das células dinamicamente
    celula *primeira = (celula *)malloc(sizeof(celula));
    celula *segunda = (celula *)malloc(sizeof(celula));
    celula *terceira = (celula *)malloc(sizeof(celula));

    //Verificação se a alocação de memória foi bem-sucedida
    if (primeira == NULL || segunda == NULL || terceira == NULL) {
        printf("Erro ao alocar memória.\n");
        return 1;
    }

    //Atribuindo valores às células
    primeira->conteudo = 10;
    primeira->prox = segunda;

    segunda->conteudo = 20;
    segunda->prox = terceira;

    terceira->conteudo = 30;
    terceira->prox = NULL;  //Fim da lista

    //Chamando a função para imprimir todos os valores da lista
    imprimeLista(primeira);

    //Liberando a memória alocada
    free(primeira);
    free(segunda);
    free(terceira);

    return 0;
}

# 3. Calcule a quantidade de memória gasta por cada instância da célula
#include <stdio.h>
#include <stdlib.h>

struct reg {
    int conteudo;
    struct reg *prox;
};

typedef struct reg celula;

//Função para imprimir todos os valores da lista encadeada!!
void imprimeLista(celula *inicio) {
    celula *p = inicio;  //ponteiro para percorrer a lista

    while (p != NULL) {  //Percorre até encontrar NULL (fim da lista)
        printf("Valor: %d\n", p->conteudo);
        p = p->prox;     //Avança para a próxima célula
    }
}

int main() {
    //impressão do tamanho da célula
    printf("Tamanho da célula: %lu bytes\n", sizeof(celula));
    //Criação das células dinamicamente
    celula *primeira = (celula *)malloc(sizeof(celula));
    celula *segunda = (celula *)malloc(sizeof(celula));
    celula *terceira = (celula *)malloc(sizeof(celula));

    //Verificação se a alocação de memória foi bem-sucedida
    if (primeira == NULL || segunda == NULL || terceira == NULL) {
        printf("Erro ao alocar memória.\n");
        return 1;
    }

    //Atribuindo valores às células
    primeira->conteudo = 10;
    primeira->prox = segunda;

    segunda->conteudo = 20;
    segunda->prox = terceira;

    terceira->conteudo = 30;
    terceira->prox = NULL;  //Fim da lista

    //Chamando a função para imprimir todos os valores da lista
    imprimeLista(primeira);

    //Liberando a memória alocada
    free(primeira);
    free(segunda);
    free(terceira);

    return 0;
}

# 4. Construa uma função que remove os elementos da lista;
#include <stdio.h>
#include <stdlib.h>

struct reg {
    int conteudo;
    struct reg *prox;
};

typedef struct reg celula;

// Função para remover (liberar) todos os elementos da lista encadeada
void removeLista(celula *inicio) {
    celula *p = inicio;      // Ponteiro auxiliar para percorrer a lista
    celula *temp;            // Ponteiro temporário para armazenar a célula a ser removida

    while (p != NULL) {
        temp = p;            // Armazena a célula atual
        p = p->prox;         // Avança para a próxima célula
        free(temp);          // Libera a célula armazenada
    }
}

int main() {
    // Criando as três células da lista encadeada dinamicamente
    celula *primeira = (celula *)malloc(sizeof(celula));
    celula *segunda = (celula *)malloc(sizeof(celula));
    celula *terceira = (celula *)malloc(sizeof(celula));

    // Verificando se a alocação de memória foi bem-sucedida
    if (primeira == NULL || segunda == NULL || terceira == NULL) {
        printf("Erro ao alocar memória.\n");
        return 1;
    }

    // Atribuindo valores às células
    primeira->conteudo = 10;
    primeira->prox = segunda;

    segunda->conteudo = 20;
    segunda->prox = terceira;

    terceira->conteudo = 30;
    terceira->prox = NULL;  // Fim da lista

    // Imprimindo os valores da lista
    printf("Antes de remover os elementos:\n");
    celula *p = primeira;
    while (p != NULL) {
        printf("Valor: %d\n", p->conteudo);
        p = p->prox;
    }

    // Removendo (liberando) todos os elementos da lista
    removeLista(primeira);

    // Após remover, a lista foi esvaziada e a memória foi liberada
    printf("Todos os elementos foram removidos.\n");

    return 0;
}

# 5. Incremente sua função liberando a memória quando um elemento é liberado;

#include <stdio.h>
#include <stdlib.h>

struct reg {
    int conteudo;
    struct reg *prox;
};

typedef struct reg celula;

// Função para remover (liberar) todos os elementos da lista encadeada
void removeLista(celula *inicio) {
    celula *p = inicio;      // Ponteiro auxiliar para percorrer a lista
    celula *temp;            // Ponteiro temporário para armazenar a célula a ser removida

    while (p != NULL) {
        temp = p;            // Armazena a célula atual
        p = p->prox;         // Avança para a próxima célula
        printf("Liberando a célula com valor: %d\n", temp->conteudo);  // Exibe o valor que está sendo liberado
        free(temp);          // Libera a célula armazenada
    }
}

int main() {
    // Criando as três células da lista encadeada dinamicamente
    celula *primeira = (celula *)malloc(sizeof(celula));
    celula *segunda = (celula *)malloc(sizeof(celula));
    celula *terceira = (celula *)malloc(sizeof(celula));

    // Verificando se a alocação de memória foi bem-sucedida
    if (primeira == NULL || segunda == NULL || terceira == NULL) {
        printf("Erro ao alocar memória.\n");
        return 1;
    }

    // Atribuindo valores às células
    primeira->conteudo = 10;
    primeira->prox = segunda;

    segunda->conteudo = 20;
    segunda->prox = terceira;

    terceira->conteudo = 30;
    terceira->prox = NULL;  // Fim da lista

    // Imprimindo os valores da lista
    printf("Antes de remover os elementos:\n");
    celula *p = primeira;
    while (p != NULL) {
        printf("Valor: %d\n", p->conteudo);
        p = p->prox;
    }

    // Removendo (liberando) todos os elementos da lista
    printf("\nRemovendo os elementos:\n");
    removeLista(primeira);

    // Após remover, a lista foi esvaziada e a memória foi liberada
    printf("Todos os elementos foram removidos e a memória liberada.\n");

    return 0;
}

# 6.Calcule o máximo de elementos possíveis na fila, considerando a memória disponível no computador.
#include <stdio.h>
#include <stdlib.h>

struct reg {
    int conteudo;
    struct reg *prox;
};

typedef struct reg celula;

int main() {
    // Define a quantidade de memória disponível (em bytes)
    unsigned long long memoria_disponivel = 8ULL * 1024 * 1024 * 1024;  // 8 GB em bytes

    // Calcula o tamanho de uma célula
    size_t tamanho_celula = sizeof(celula);

    // Calcula o número máximo de células que podem ser alocadas
    unsigned long long max_elementos = memoria_disponivel / tamanho_celula;

    // Exibe o resultado
    printf("Memória disponível: %llu bytes\n", memoria_disponivel);
    printf("Tamanho de cada célula: %zu bytes\n", tamanho_celula);
    printf("Número máximo de elementos que podem ser armazenados na lista: %llu\n", max_elementos);

    return 0;
}




