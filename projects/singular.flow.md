# Primer para uma app de geração de música

*Eu trabalho com redes neuronais, portanto vai ser tudo enviesado para isso. Isto não é necessariamente para Dark Ambient, mas é uma espécie de uma framework que podia ser adaptado para uma série de "instrumentos" diferentes*

A - Timbre
---
**Algoritmo e Arquitectura**

*Um modelo do mundo*

Usar um modelo capaz de codificar a informação numa distribuição e descodificar informação a partir dessa distribuição. Isto servirá vários propósitos:

1. Permite o treino mais facilitado (e muito mais rápido) de um modelo generativo ao usar uma representação latente de baixas dimensões
2. Ao criarmos um modelo descodificador, vamos condicioná-lo às amostras que lhe apresentamos - isto enviesa toda a geração para a mesma "palete de sons" e conseguimos transformar um som em algo completamente diferente (i.e. se condicionarmos o modelo com o som de um piano e usarmos como input um cão a ladrar, o output não vai ser remotamente semelhante ao cão mas sim a versão do modelo (piano) de um cão a ladrar)
3. Tornamos a geração de novos sons (dentro de uma palete de sons) mais fácil por podermos apenas samplar de cada distribuição
4. Acrescentamos mais uma camada de interação ao possibilitar que sons externos sejam transformados na palete de sons que usámos para treinar o algoritmo
5. Caso usemos um variational autoencoder (VAE - rede neuronal que faz isto), podemos usar uma propriedade interessante que os VAE têm - a representação latente tem uma certa aritmética que permite ao mesmo modelo combinar duas caracteristicas com que foi treinado ao fazer a média de duas representações latentes (i.e. fazer a média entre um trombone e um trompete dá, em teoria, uma coisa no meio)

* "Add-ons" 
	* Como é uma distribuição estatística podemos alterar alguns parâmetros que digam respeito à "dispersão" e aumentar a imprevisibilidade da coisa
	* Podemos também "matar" uma das dimensões (sempre igual a 0)? Não sei o que é que isto faz, mas não pode ser terrível
	* Criar uma cena para o utilizador ter à frente a distribuição atual e poder mexer-lhe para cima e para baixo 

*Um mapa do mundo*

Acho que era importante ter também uma funcionalidade que permitisse à app gerar música por ela mesma *ad nauseum*. Há uma série de abordagens para isto. Eu (mais uma vez) sugeria usar redes neuronais (RNN, LSTM), a implementação não é extremamente complicada e costumam dar os melhores resultados possíveis

B - Instrumento
---
A partir do timbre podemos usar um pad para variar a frequência e botões que dêem para "centrar" o timbre numa nota para tornar a coisa mais "tocável" do ponto de vista melódico e quantizar cenas em notas

* "Add-ons" 
	* Efeitos especiais (delays e reverbs e por aí adiante)
	* Equalizador

C - O next step da coisa
---
A parte fixe das representações latentes é que muita coisa pode ter uma representação latente - incluindo imagens. Portanto, em teoria, podemos usar imagens para definir o timbre ao criar um codificador para as imagens e usar som, e podemos usar som para criar imagens, usando um descodificador de imagens com som. Não via isto numa app, mas via isto na boa num cenário mais performático, aliado a uma cena toda avant-garde CITAC e por aí ou coreografia ou whatever