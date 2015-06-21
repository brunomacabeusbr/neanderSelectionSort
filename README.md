neanderSelectionSort
======================

Algorítio de selection sort para <a href="https://pt.wikipedia.org/wiki/M%C3%A1quinas_hipot%C3%A9ticas_da_Universidade_Federal_do_Rio_Grande_do_Sul#Neander">Neander</a>

*Considere todos os valores numéricos abaixo como hexadecimais*

*Considere LA como a lista que será ordenada e LB como a lista que armazena os valores que já foram ordenados*

Para usar
-----------
Altere os valores da memória de 83..87 para os números que queira que sejam ordenados.
Use apenas valores de 01 até 7F.

O resultado da lista ordenada estará nos registradores 91..96

Explicação
----------
**Algorítimo**

0. Seleciona o último elemento da LA
0. Efetua um loop com cada valores da LA analisando se é maior que esse número selecionado
0. Se for encontrado um valor maior que ele, este passa a ser o número selecionado
0. Ao terminar de pecorrer todos os valores da LA, adiciona o número selecionado ao final da LB e altera o número selecionado na lista LA para FF
0. Efetua novamente o primeiro passo, selecionando o número anterior ao selecionado, até que se termine de pecorrer toda a lista LA

Saber se o número é maior que o outro

0. Dê `load` no número alvo
0. Efetue a instrução `not`
0. Dê `add` somando 1
0. Então dê `add` no número que queira saber se é maior ou não em relação ao número alvo
0. Se o resultado for negativo, é maior, caso contrário, é menor, se zero, igual

**Uso da memória**

* 7E → constante para da +1 (usado para saber se o número é maior ou não)
* 7F → controle do loop interno (algorítimo 2..3)
* 80 → controle do loop maior (algorítimo 1..5)
* 81 → constante para da -1 (controle de loop) e usar o FF (algorítimo 3)
* 82 → tamanho da lista LA
* 83..87 → lista LA
* 8A → constante do endereço de onde começa a lista LA
* 8C → numero da lista a saber se é o maior ou não (algorítimo 2..3)
* 8D → posição do maior numero do loop até o momento (algorítimo 2..3)
* 8E → temp do número que será analisado (algorítimo 2..3)
* 90 → constante do endereço de onde começa a lista LB
* 91..96 → lista LB

**Explicações das instruções**

* 00..0B → Início do loop maior
* 0C..18 → Pegar o próximo elemento da lista LA. Se for da flag negativa, passa para o próximo. Caso contrário, salva a posição dele em 8D e o valor em 8C.
* 19..26 → Início do loop interno
* 27..2F → Pegar o próximo elemento da lista no loop interno e salva em 8E
* 30..42 → Verificação para saber o próximo maior número. Se for, armazena a posição dele em 8D e valor em 8C
* 43..44 → Fim do loop interno
* 46..57 → Por número na lista organizada e alterar o valor dele na lista a ser organizada para um negativo, como flag
* 59..5E → Fim do loop maior
* 60 → Encerra a aplicação

TODO
----
- [ ] Organizar código seguindo as convenções do Neander (instruções de 00..7F e dados 80..FF)
- [ ] Refatorar código para deixa-lo organizado
- [ ] Permitir usar listas de tamanhos variados