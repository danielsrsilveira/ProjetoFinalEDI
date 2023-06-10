#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Definição da estrutura do Contato
typedef struct {
    char nome[50];
    char email[50];
    char cpf[12];
    char telefone[15];
} Contato;

// Definição da estrutura do Nodo da lista
typedef struct Nodo {
    Contato contato;
    struct Nodo* proximo;
    struct Nodo* anterior;
} Nodo;

// Definição da estrutura da Lista Duplamente Encadeada com Header
typedef struct {
    Nodo* cabecalho;
    int tamanho;
} Lista;

// Função para criar uma nova lista vazia
Lista* criarLista() {
    Lista* novaLista = (Lista*)malloc(sizeof(Lista));
    novaLista->cabecalho = NULL;
    novaLista->tamanho = 0;
    return novaLista;
}

// Função para criar um novo nodo com um contato
Nodo* criarNodo(Contato contato) {
    Nodo* novoNodo = (Nodo*)malloc(sizeof(Nodo));
    novoNodo->contato = contato;
    novoNodo->proximo = NULL;
    novoNodo->anterior = NULL;
    return novoNodo;
}

// Função para inserir um contato na posição correta da lista (ordem alfabética do CPF)
void inserirContato(Lista* lista, Contato contato) {
    Nodo* novoNodo = criarNodo(contato);

    if (lista->cabecalho == NULL) {
        lista->cabecalho = novoNodo;
    } else {
        Nodo* nodoAtual = lista->cabecalho;
        Nodo* nodoAnterior = NULL;

        while (nodoAtual != NULL && strcmp(nodoAtual->contato.cpf, contato.cpf) < 0) {
            nodoAnterior = nodoAtual;
            nodoAtual = nodoAtual->proximo;
        }

        if (nodoAnterior == NULL) {
            novoNodo->proximo = lista->cabecalho;
            lista->cabecalho->anterior = novoNodo;
            lista->cabecalho = novoNodo;
        } else {
            novoNodo->proximo = nodoAtual;
            novoNodo->anterior = nodoAnterior;
            nodoAnterior->proximo = novoNodo;

            if (nodoAtual != NULL) {
                nodoAtual->anterior = novoNodo;
            }
        }
    }

    lista->tamanho++;
}

// Função para remover um contato de uma posição específica da lista
void removerContato(Lista* lista, int posicao) {
    if (posicao < 0 || posicao >= lista->tamanho) {
        printf("Posicao invalida!\n");
        return;
    }

    Nodo* nodoAtual = lista->cabecalho;
    Nodo* nodoAnterior = NULL;
    int contador = 0;

    while (nodoAtual != NULL && contador < posicao) {
        nodoAnterior = nodoAtual;
        nodoAtual = nodoAtual->proximo;
        contador++;
    }

    if (nodoAnterior == NULL) {
        lista->cabecalho = nodoAtual->proximo;

        if (nodoAtual->proximo != NULL) {
            nodoAtual->proximo->anterior = NULL;
        }
    } else {
        nodoAnterior->proximo = nodoAtual->proximo;

        if (nodoAtual->proximo != NULL) {
            nodoAtual->proximo->anterior = nodoAnterior;
        }
    }

    free(nodoAtual);
    lista->tamanho--;
}

// Função para consultar um contato em uma posição específica da lista
void consultarContato(Lista* lista, int posicao) {
    if (posicao < 0 || posicao >= lista->tamanho) {
        printf("Posicao invalida!\n");
        return;
    }

    Nodo* nodoAtual = lista->cabecalho;
    int contador = 0;

    while (nodoAtual != NULL && contador < posicao) {
        nodoAtual = nodoAtual->proximo;
        contador++;
    }

    printf("Contato na posicao %d:\n", posicao);
    printf("Nome: %s\n", nodoAtual->contato.nome);
    printf("E-mail: %s\n", nodoAtual->contato.email);
    printf("CPF: %s\n", nodoAtual->contato.cpf);
    printf("Telefone: %s\n", nodoAtual->contato.telefone);
}

// Função para listar todos os contatos da lista
void listarContatos(Lista* lista) {
    if (lista->tamanho == 0) {
        printf("Lista vazia!\n");
        return;
    }

    Nodo* nodoAtual = lista->cabecalho;

    printf("Lista de Contatos:\n");

    while (nodoAtual != NULL) {
        printf("Nome: %s\n", nodoAtual->contato.nome);
        printf("E-mail: %s\n", nodoAtual->contato.email);
        printf("CPF: %s\n", nodoAtual->contato.cpf);
        printf("Telefone: %s\n", nodoAtual->contato.telefone);

        printf("Endereco: %p\n", nodoAtual);
        printf("Proximo: %p\n", nodoAtual->proximo);
        printf("Anterior: %p\n", nodoAtual->anterior);

        printf("-----------------------\n");

        nodoAtual = nodoAtual->proximo;
    }
}

// Função para liberar a memória alocada pela lista e seus nodos
void liberarLista(Lista* lista) {
    Nodo* nodoAtual = lista->cabecalho;
    Nodo* nodoAnterior = NULL;

    while (nodoAtual != NULL) {
        nodoAnterior = nodoAtual;
        nodoAtual = nodoAtual->proximo;
        free(nodoAnterior);
    }

    free(lista);
}

int main() {
    Lista* lista = criarLista();

    // Exemplo de inserção de contatos
    Contato contato1 = {"Fulano", "fulano@example.com", "12345678900", "(00) 1234-5678"};
    Contato contato2 = {"Ciclano", "ciclano@example.com", "98765432100", "(11) 9876-5432"};
    Contato contato3 = {"Beltrano", "beltrano@example.com", "45678912300", "(22) 4567-8901"};
    Contato contato4 = {"Zulano", "zulano@example.com", "78912345600", "(33) 7890-1234"};
    Contato contato5 = {"Xablau", "xablau@example.com", "11111111111", "(44) 1111-1111"};

    inserirContato(lista, contato1);  // Inserção no começo
    inserirContato(lista, contato2);  // Inserção no meio
    inserirContato(lista, contato3);  // Inserção no meio
    inserirContato(lista, contato4);  // Inserção no final
    inserirContato(lista, contato5);  // Inserção no começo

    // Exemplo de remoção de contatos
    removerContato(lista, 2);  // Remoção no meio
    removerContato(lista, 0);  // Remoção no começo
    removerContato(lista, 3);  // Remoção no final

    // Exemplo de consulta de contatos
    consultarContato(lista, 1);

    // Listar todos os contatos
    listarContatos(lista);

    liberarLista(lista);

    return 0;
}
