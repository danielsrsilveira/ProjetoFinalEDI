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
