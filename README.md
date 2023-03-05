# StenographicImg

Este programa é feito para comunicação usando estenografia, a estenografia é a arte ou técnica de escrever em caracteres ou símbolos ocultos ou abreviados para transmissão de informações de forma secreta ou para economizar tempo ou espaço. No caso queremos codificar uma mensagem dentro de uma foto.

O princípio básico de funcionamento do é o seguinte:

    1. Uma mensagem é escrita no arquivo "mensagem.txt", essa mensagem é codificada para binário em 8bits no arquivo "codificador.py", na seguinte linha de código: "msg_bin = ''.join(format(ord(i), '08b') for i in msg)";
    
    2. Uma vez codificada a mensagem, o codificador extrai todos os pixels da imagem (fonte.png) no formato RGBA e converte a informação para binário;

    3. O codificador passa cada pixel alterando os dados dos 2 LSB de cada bit, a alteração é feita de modo a implantar a mensagem na imagem. Esse conceito é melhor entendido por um exemplo:
        primeiro pixel: [(10111001),(0101011),(0111011),(0101111)]
        primeiros byte da mensagem: 10101011
        Como o programa altera píxel: [(10111001),(0101011),(0111011),(0101111)] -> [(10111010),(0101010),(0111010),(0101111)]
        Dessa forma, a informação do primeiro byte da mensagem foi inserida no primeiro píxel da foto, causando alterações mínimas na mesma
    4. Uma vez que toda a mensagem foi codificada na imagem, uma nova imagem é gerada contendo a mensagem.
    5. Usando essa nova imagem como entrada no "decodificador.py", o programa faz o processo reverso e extrai a mensagem da foto, exibindo ela no arquivo "decodificado.txt".

Esse tipo de programa pode ser utilizado para comunicação furtiva, mas está sujeito a erros caso o arquivo seja comprimido ou convertido de alguma forma, ainda falta debugar alguns erros de comunicação que ocorrem quando caracteres muito estranhos são usados, mas ele já serve ao propósito que foi criado.

Criei esse programa para me desafiar depois que vi o vídeo do canal computerphyle: https://www.youtube.com/watch?v=TWEXCYQKyDc

(quando estava criando esse README.md descobri que o nome verdadeiro da técnica é steganography, mas fiquei com preguiça de mudar, fica estenografia mesmo (y)).
