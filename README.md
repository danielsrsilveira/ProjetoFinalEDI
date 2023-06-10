# ProjetoFinalEDI
Trabalho Final – Estrutura de Dados I 

-       Em grupos de até 3 pessoas;

-       Gravar um vídeo de 8 a 15 minutos

-       O vídeo deverá apresentar o código, rodar os casos de teste

- Entrega dia 28/06/2023 até 23h59

 

Situação problema: Armazenar lista de contatos (Nome, E-mail, CPF, Telefone); Sem quantitativo máximo.

1 - Os dados devem ficar armazenados em uma Lista duplamente Encadeada com Header; 

2 – O usuário irá inserir os contatos, o programa deverá colocar, no momento da inserção, na posição correta; conforme ordem ALFABÉTICA do CPF (considerar como string) . Considerar que não haverá CPFs repetidos;

A implementação da lista deverá permitir (pelo menos), através de menu de acesso, realizar as operações:

a- Inserir em qualquer posição (começo, meio ou final), conforme ordem alfabética do CPF. O usuário informa os dados do contato e o programa insere na lista, na posição correta.

b- Remover itens de qualquer posição (começo, meio ou final);

c- Consultar itens de qualquer posição;

d- Listar os itens da lista; (Percorrer a lista). Sugestão: quando listar todos os itens, incluir os endereços do item, próximo nodo e nodo anterior para cada item. 

1 - descrever em Português (no vídeo) o processo que deve acontecer em cada um dos itens (a,b,c,d);
2 - descrever quais problemas podem ocorrer nos itens (a,b,c,d); (se houver);
3 - descrever (pelo menos) um caso de teste para cada item (a,b,c,d) que permitam saber se estes estão funcionando adequadamente;
4 – demonstrar inserção de (pelo menos 5 elementos), demonstrando inserções no começo, meio e final;
5 – demonstrar remoção de (pelo menos 3 elementos), demonstrando remoções no começo, meio e final;
6 - demonstrar outras situações com possibilidade de erros.

Enviar o link do vídeo (texto) E códigos-fonte anexos.

Dicas:
a - não usar atribuição (=) para copiar strings, use strcpy;
b - implemente uma lista que tenha uma função que permita inserir em qualquer posição
c - implemente uma função que identifique qual a posição um registro deve ser inserido para manter a ordem alfabética, por exemplo int posicao(Lista *l, char cpf[]);
d - usando a posição descoberta na dica c, insira o contato na posição correta com a função da dica b;

Material strings, ordem alfabética:
https://docs.google.com/presentation/d/1XlDy5KNN2HrbIcn3nBvt0UjBHLuN7NWWwz3B1D0-Z9Y/edit#slide=id.g3ef17badb0_0_554

O código implementa uma lista duplamente encadeada com header para armazenar contatos. 

Código em detalhes:

    As bibliotecas stdio.h, stdlib.h e string.h são incluídas para usar funções de entrada/saída, alocação dinâmica de memória e manipulação de strings, respectivamente.

    A estrutura Contato é definida para armazenar informações sobre um contato, incluindo nome, email, CPF e telefone.

    A estrutura Nodo é definida para representar cada elemento da lista. Ela contém um campo contato do tipo Contato e dois ponteiros, proximo e anterior, que apontam para os nodos adjacentes.

    A estrutura Lista é definida para manter o controle da lista. Ela possui um ponteiro cabecalho que aponta para o primeiro nodo da lista (o header) e um inteiro tamanho que armazena o número de elementos na lista.

    A função criarLista cria e retorna uma nova lista vazia. Ela aloca memória para a estrutura Lista, inicializa o campo cabecalho como NULL e o campo tamanho como zero.

    A função criarNodo cria e retorna um novo nodo com um contato fornecido como parâmetro. Ela aloca memória para a estrutura Nodo, atribui o contato ao campo contato do nodo e inicializa os ponteiros proximo e anterior como NULL.

    A função inserirContato insere um contato na posição correta da lista, mantendo a ordem alfabética do CPF. Ela recebe a lista e o contato a ser inserido como parâmetros. A função cria um novo nodo com o contato fornecido. Em seguida, percorre a lista para encontrar a posição correta de inserção com base no CPF. O novo nodo é inserido na posição correta, ajustando os ponteiros proximo e anterior dos nodos adjacentes.

    A função removerContato remove um contato de uma posição específica da lista. Ela recebe a lista e a posição do contato a ser removido como parâmetros. A função verifica se a posição é válida. Em seguida, percorre a lista até o nodo correspondente à posição e realiza a remoção, ajustando os ponteiros proximo e anterior dos nodos adjacentes. A memória alocada para o nodo removido é liberada.

    A função consultarContato consulta um contato em uma posição específica da lista. Ela recebe a lista e a posição do contato a ser consultado como parâmetros. A função verifica se a posição é válida. Em seguida, percorre a lista até o nodo correspondente à posição e exibe as informações do contato.

    A função listarContatos exibe todos os contatos da lista. Ela recebe a lista como parâmetro. A função percorre a lista, começando pelo nodo cabeçalho, e exibe as informações de cada contato.

    A função liberarLista libera a memória alocada pela lista e seus nodos. Ela recebe a lista como parâmetro. A função percorre a lista, liberando a memória de cada nodo, e depois libera a memória da estrutura Lista em si.

    A função main é a função principal do programa. Ela cria uma nova lista chamando criarLista(). Em seguida, são adicionados alguns contatos à lista usando a função inserirContato. São feitas chamadas às funções removerContato, consultarContato e listarContatos para demonstrar as operações na lista. Por fim, a memória alocada pela lista é liberada chamando liberarLista(lista).
