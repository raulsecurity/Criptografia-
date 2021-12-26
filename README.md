1
Transcrição de vídeo
Criptografia: Crash Course Computer Science #33
Olá, eu sou a Carrie Anne, bem-vindos ao Crash Course Computer Science!
Nos últimos dois episódios, falamos muito sobre segurança computacional. Mas a verdade é que não
existe um sistema computacional 100% seguro. Sempre haverá erros e os especialistas em segurança
sabem disso.
Por isso, os arquitetos de sistemas empregam uma estratégia chamada defesa em profundidade, que
usa muitas camadas de mecanismos de segurança variados para combater os invasores. Funciona mais
ou menos como os castelos e a maneira como eles são projetados. Primeiro, é necessário desviar dos
arqueiros, depois, atravessar o fosso, escalar as paredes, evitar o óleo quente, ultrapassar as muralhas
e derrotar os guardas antes de chegar à sala do trono. No entanto, neste caso, estamos falando de uma
das formas mais comuns da segurança computacional, a criptografia.
INTRODUÇÃO
Na etimologia da palavra criptografia estão as raízes “cripto” e “grafia”, ou seja, “escrita secreta”. Para
tornar as informações secretas, uma cifra é usada, um algoritmo que converte texto sem formatação em
texto cifrado e que não faz sentido sem a chave que permite desfazer essa cifra. O processo de
transformar textos em secretos é chamado de criptografia e o processo inverso é chamado de
decriptografia.
As cifras eram usadas muito antes dos computadores surgirem. Júlio César usou o que agora é chamado
de cifra de César, a fim de criptografar sua correspondência privada. Ele trocava cada letra pela terceira
próxima letra no alfabeto. Portando, “D” substituiria “A”, e uma palavra como “brutus” era escrita dessa
forma: “euxwxv”.
Para decifrar a mensagem, os destinatários precisavam saber o algoritmo e o número de trocas de
letras, que funcionavam como a chave. A cifra de César é um exemplo de uma classe maior de técnicas
denominadas cifras de substituição. Elas substituem cada letra de uma mensagem por outra, de acordo
com a tradução.
Uma grande desvantagem das cifras básicas de substituição é que as frequências de letras são
preservadas. Por exemplo, “E” é a letra mais comum em inglês, portanto, se sua cifra converte “E” em
“X”, então a letra “X” será exibida com mais frequência no texto cifrado. Um criptoanalista qualificado
pode trabalhar de trás para frente com esses tipos de estatísticas para descobrir a mensagem. Foi a
descoberta de uma cifra de substituição que levou à execução de Maria, rainha dos escoceses, em
1587, por tramar o assassinato da rainha Elizabeth.
Outra classe fundamental de técnicas são as cifras de permutação. Vejamos um exemplo simples,
chamado de cifra de transposição colunar. Aqui, utilizamos uma mensagem e preenchemos as letras em
uma grade. Neste caso, escolhemos 5 por 5. Para criptografar nossa mensagem, lemos os caracteres
em uma ordem diferente, por exemplo, do canto inferior esquerdo para cima, uma coluna por vez. A
nova ordem das letras, chamada de permutação, é a mensagem criptografada. A direção e o tamanho da
grade de 5 por 5 funcionam como a chave. Assim como antes, se a cifra e a chave forem descobertas,
um destinatário pode reverter o processo para revelar a mensagem original. 
2
Nos anos 1900, a criptografia foi mecanizada na forma de máquinas de criptografia. A mais famosa foi a
Enigma da Alemanha, usada pelos nazistas para criptografar suas comunicações em tempos de guerra.
Como discutimos no episódio 15, a Enigma era parecida com uma máquina de escrever, com um teclado
e um quadro de lâmpadas, ambos mostrando o alfabeto completo. Acima, havia uma série de rotores
configuráveis que eram a chave para o recurso de criptografia da Enigma.
Primeiro, vamos ver somente um rotor. Um lado tinha contatos elétricos para todas as 26 letras. Eles se
conectavam ao outro lado do rotor usando fios de cruzamento que trocavam uma letra por outra. Se “H”
entrasse por um lado, “K” poderia sair pelo outro. Se “K” entrasse, “F” poderia sair e assim por diante.
Esse comportamento de troca de letras parece familiar: é uma cifra de substituição! Mas a Enigma era
mais sofisticada porque usava três ou mais rotores seguidos, cada um alimentando o próximo.
Os rotores também podiam ser rotacionados para uma das 26 possíveis posições iniciais e inseridos em
diferentes ordens, fornecendo muitos mapeamentos de substituição diferentes. Seguindo os rotores,
havia um circuito especial chamado refletor. Em vez de transmitir o sinal para outro rotor, ele conectava
cada pino a outro e enviava o sinal elétrico de volta através dos rotores. Finalmente, havia um painel de
controle na parte frontal da máquina que permitia que as letras vindas do teclado fossem trocadas,
opcionalmente, incluindo outro nível de complexidade.
Com nosso circuito simplificado, vamos criptografar uma carta neste exemplo de configuração da
Enigma. Se pressionarmos a tecla “H”, a eletricidade flui através do painel de controle, em seguida, os
rotores atingem o refletor, retornam através dos rotores e do painel de distribuição e acendem a letra
“L” no quadro de lâmpadas. Portanto, “H” é criptografado em “L”. Observe que o circuito pode fluir nos
dois sentidos, portanto, ao digitarmos a letra “L”, “H” acenderá.
Em outras palavras, é o mesmo processo para criptografar e decriptografar. Basta garantir que as
máquinas de envio e recebimento tenham a mesma configuração inicial. Ao observar atentamente esse
circuito, você perceberá que é impossível que uma letra seja criptografada como ela mesma, o que
acabou sendo uma fraqueza criptográfica fatal.
Finalmente, para evitar que a Enigma fosse uma cifra de substituição simples, toda vez que uma letra
era inserida, os rotores avançavam uma posição, como um hodômetro em um carro.
Portanto, se o texto A-A-A fosse digitado, ele poderia aparecer como B-D-K, pois o mapeamento de
substituição era mudado ao pressionar cada tecla. A Enigma era definitivamente difícil de decifrar. Mas,
como discutimos no episódio 15, Alan Turing e seus colegas de Bletchley Park conseguiram quebrar os
códigos da Enigma e automatizar amplamente o processo.
No entanto, com o advento dos computadores, a criptografia passou do hardware para o software. Uma
das primeiras cifras de software a se difundir foi o Padrão de Criptografia de Dados desenvolvido pela
IBM e a NSA em 1977. O DES, como era conhecido, originalmente usava chaves binárias com 56 bits de
comprimento, o que significa que existem 2 elevado a potência de 56 ou cerca de 72 quadrilhões de
chaves diferentes.
Em 1977, isso significava que ninguém (exceto, talvez, a NSA) tinha poder computacional suficiente
para forçar brutalmente todas as chaves possíveis. Mas, em 1999, um computador de 250 milhões de
dólares poderia testar todas as chaves DES possíveis em apenas dois dias, tornando a cifra insegura.
Assim, em 2001, o Padrão de Criptografia Avançado (AES) foi finalizado e publicado. O AES foi projetado
para usar chaves muito maiores (128, 192 ou 256 bits), dificultando muito mais os ataques de força 
3
bruta. Para chaves de 128 bits, trilhões de anos seriam necessários para testar todas as combinações,
mesmo se todos os atuais computadores do planeta fossem usados. Então, é melhor começar logo!
O AES divide os dados em blocos de 16 bytes e, em seguida, aplica uma série de substituições e
permutações com base no valor da chave, além de outras operações para ocultar a mensagem, e esse
processo é repetido dez ou mais vezes para cada bloco. Você pode estar se perguntando: por que
somente dez rodadas? ou por que somente chaves de 128 bits, em vez de chaves de dez mil bits? O
motivo é o desempenho. Se levasse horas para criptografar e enviar um e-mail ou minutos para se
conectar a um site seguro, as pessoas não o usariam.
O AES equilibra desempenho e segurança para fornecer criptografia prática. Hoje, o AES é usado em
todos os lugares, desde a criptografia de arquivos em iPhones e a transmissão de dados via wi-fi com
WPA2 até o acesso a sites por meio de HTTPS.
Até agora, as técnicas criptográficas discutidas dependem de chaves conhecidas pelo remetente e pelo
destinatário. O remetente criptografa uma mensagem usando uma chave e o destinatário a
decriptografa usando a mesma chave. Antigamente, as chaves eram compartilhadas fisicamente ou
ditas, por exemplo, os alemães distribuíam livros de códigos com configurações diárias para suas
máquinas Enigma. No entanto, essa estratégia nunca funcionaria na era da Internet. Imagine ter que
abrir um livro de códigos para se conectar ao YouTube!
O que é necessário para que um servidor envie uma chave secreta pela Internet pública a um usuário
que deseja se conectar com segurança? Parece que isso não seria seguro porque se a chave fosse
enviada abertamente e interceptada por um hacker, ele poderia usá-la para decriptografar toda a
comunicação.
A solução é a troca de chaves! Um algoritmo que permite que dois computadores concordem com uma
chave sem que ela seja enviada. Podemos fazer isso com funções unidirecionais, ou seja, operações
matemáticas que são muito fáceis de fazer em uma direção, mas difíceis de reverter.
Para mostrar como as funções unidirecionais funcionam, vamos usar cores de tintas como analogia. É
fácil misturar cores de tintas, mas não é tão fácil assim descobrir as cores usadas para criar uma cor de
tinta mista. Seria necessário testar muitas possibilidades para descobrir isso.
Nesta metáfora, nossa chave secreta é um tom de tinta específico. Primeiro, há uma cor de tinta pública
que todos podem ver. Em seguida, John e eu escolhemos uma cor de tinta secreta. Para trocar chaves,
misturo minha cor de tinta secreta com a cor pública. Então, envio essa cor mista para John por
qualquer meio, e-mail, pombo-correio, o que for. John faz o mesmo, mistura sua cor de tinta secreta
com a cor pública e, em seguida, envia isso para mim. Quando recebo a cor de John, simplesmente
incluo minha cor específica para criar uma mistura das três tintas. John faz o mesmo com minha cor
mista. E Pronto! Nós dois acabamos com a mesma cor de tinta!
Podemos usar isso como um segredo compartilhado, mesmo que nunca tenhamos enviado nossas cores
secretas individuais. Um observador externo saberia informações parciais, mas teria muita dificuldade
para descobrir nossa cor secreta compartilhada. Obviamente, enviar e misturar cores de tinta não
funcionará bem na transmissão de dados de computador. Mas, felizmente, as funções matemáticas
unidirecionais são perfeitas e é isso que o Diffie-Hellman Key Exchange usa.
No Diffie-Hellman, a função unidirecional é a exponenciação modular. Isso significa elevar um número, a
base, à potência de outro número, o expoente, e dividir o restante por um terceiro número, o módulo. 
4
Assim, por exemplo, se quiséssemos calcular 3 à 5ª potência, módulo 31, calcularíamos 3 à 5ª potência,
que é 243, e dividiríamos o restante por 31, que é 26.
A parte difícil é descobrir o expoente tendo apenas o resultado e a base. Se eu disser que elevei 3 a
algum número secreto, módulo 31, e obtiver 7 como o restante, você teria que testar muitos expoentes
para saber qual deles eu escolhi. Se aumentarmos esses números, digamos, centenas de dígitos,
encontrar o expoente secreto será praticamente impossível.
Agora, vamos falar sobre como Diffie-Hellman usa a exponenciação modular para calcular uma chave
compartilhada. Primeiro, há um conjunto de valores públicos, a base e o módulo, que, como nossa cor
de tinta pública, todos conhecem... até os criminosos!
Para enviar uma mensagem com segurança para John, eu escolheria um expoente secreto: X. Em
seguida, elevaria B à potência de X, módulo M, e enviaria este número grande a John. John faria o
mesmo, escolhendo um expoente secreto Y e enviando-me B elevado a Y, módulo M. Para criar uma
chave secreta compartilhada, eu elevaria o que John me enviou à potência de X, meu expoente secreto.
Isso seria matematicamente equivalente a elevar B à potência de XY, módulo M.
John faria o mesmo, elevando o que enviei a ele à potência de Y, e nós dois terminaríamos exatamente
com o mesmo número! É uma chave compartilhada secreta, mesmo que nunca tenhamos enviado um
ao outro nosso número secreto. Podemos usar esse número grande como uma chave compartilhada
para a comunicação criptografada, usando algo como o AES para a criptografia.
A troca de chaves de Diffie-Hellman é um método para estabelecer uma chave compartilhada. Essas
chaves que podem ser usadas pelo remetente e pelo destinatário para criptografar e decriptografar
mensagens são chamadas de chaves simétricas porque a chave é a mesma nos dois lados. A cifra de
César, a Enigma e o AES são todos criptografia simétrica.
Também existe a criptografia assimétrica, na qual existem duas chaves diferentes, geralmente, uma que
é pública e outra que é privada. Dessa forma, as pessoas podem criptografar uma mensagem usando
uma chave pública que somente o destinatário, com sua chave privada, pode decriptografar. Em outras
palavras, saber a chave pública permite apenas criptografar, mas não decriptografar, por isso é
assimétrico!
Tendo isso em mente, pense em caixas com cadeados que podem ser abertos com uma chave. Para
receber uma mensagem segura, posso dar ao remetente uma caixa e um cadeado. Ele coloca a
mensagem lá e tranca a caixa. Agora, ele pode enviar a caixa de volta para mim e somente eu poderei
abri-la, com minha chave privada. Depois de trancar a caixa, nem o remetente nem ninguém que a
encontre poderá abri-la sem força bruta. Da mesma forma, uma chave pública digital pode criptografar
algo que só pode ser decriptografado com uma chave privada. O inverso também é possível: criptografar
algo com uma chave privada que pode ser decriptografado com uma chave pública.
Isso é usado para assinaturas, nas quais um servidor criptografa dados usando sua própria chave
privada. Qualquer pessoa pode decriptografá-los usando a chave pública do servidor. Isso funciona
como uma assinatura única, pois somente o proprietário, usando sua chave privada, pode criptografar.
Isso prova que você está obtendo dados da pessoa ou servidor correto, não de um impostor.
A técnica de criptografia assimétrica mais popular usada hoje em dia é a RSA, nomeada em homenagem
aos seus inventores: Rivest, Shamir e Adleman. Bom, agora você conhece todas as partes “chave“ da
criptografia moderna: criptografia simétrica, troca de chaves e criptografia de chave pública. Ao se 
5
conectar a um website seguro, como o do seu banco, esse pequeno ícone de cadeado significará que
seu computador usou a criptografia de chave pública para verificar o servidor, a troca de chaves para
estabelecer uma chave temporária secreta e a criptografia simétrica para proteger toda a comunicação
contra olhares indiscretos.
Independentemente de você estar comprando algo on-line, enviando e-mails para amigos ou somente
vendo vídeos de gatos fofos, a criptografia manterá tudo isso seguro, privado e protegido. Obrigada,
criptografia!
