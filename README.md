# Introdução

Em web existem dois modelos de organização de layout: o modelo de caixas flexíveis e o de grade (este último usado por bibliotecas de estilo prontas).

O modelo de caixas flexíveis já vem como padrão: não é preciso declarar nada extra para usá-lo.


# Contêiner e filhos

Vale ter sempre em mente a ideia de elemento pai (contêiner) e elementos filhos.

É simples de visualizar:

```
<View>
    <Text></Text>
    <View>
        <Text></Text>
        <Text></Text>
    </View>
</View>
```

O componente de exibição mais externo tem dois filhos: um de texto e outro de exibição. O interno tem dois de texto e é filho do externo. A mesma ideia vale para os demais componentes.


# Exemplo com duas caixas

Neste exemplo foram desenhadas duas caixas na tela, uma vermelha e uma azul, alinhadas na vertical.

As caixas são componentes de exibição. Lembrando a estrutura básica: primeiro se declara uma função por caixa. Parte do código, declarando uma das duas funções:

![example with two boxes](images/exemplo-com-duas-caixas.png)

Depois, usa-se o componente criado pela função:

![using the components created with the functions](images/usando-componentes-criados.png)

E como esse exemplo usa o componente de exibição dentro da função, não esqueça de importá-lo.

```
import {View} from 'react-native';   
```

Resultado no emulador:

![result in emulator](images/resultado-no-emulador.png)


# Flexão

Como se viu no exemplo anterior, as caixas internas ficam dentro de uma caixa externa: a aplicação precisa de um único componente raiz.

E se removermos a flexão da configuração do contêiner?

![removing flex: 1 of the container](images/sem-flexao-no-conteiner.png)

Nota: neste teste o contêiner externo ficou com borda roxa.

Também é possível pôr a flexão em uma das caixas:

![inserting flex: 1 in one of the boxes](images/flexao-na-vermelha.png)

Explicação: a caixa vermelha ocupa toda a área vertical que não estiver tomada pela azul.

O mesmo raciocínio vale aumentando a altura da caixa azul:

![increasing the height of the blue box](images/altura-maior-na-azul.png)

E se a flexão for colocada também na caixa azul?

![flex: 1 in the blue box](images/flexao-na-azul.png)

Para a caixa azul ocupar toda a largura, ajuste a largura na configuração de estilo:

![width 100% in blue box](images/azul-com-largura-total.png)

Repare que, quando a unidade não é informada, o valor se comporta como pixel.

Com quatro caixas na vertical, cada uma fica com um quarto da área:

![4 boxes](images/quatro-caixas.png)

E com duas caixas de altura 100 mais uma azul flexível:

![3 boxes](images/tres-caixas.png)


# Direção das caixas

O valor padrão dessa configuração é coluna, mas dá para trocar para linha:

![flex direction row](images/direcao-em-linha.png)

Comentário: coluna é o padrão aqui, enquanto na web o padrão é linha.

Não definir nada ou definir coluna dá o resultado esperado:

![flex direction column](images/direcao-em-coluna.png)

Existem outros valores, como o de coluna invertida:

![flex direction column reverse](images/coluna-invertida.png)

Detalhe que confunde: **o nome da configuração usa formato camelo (direçãoEmLinha), mas o valor usa hífen (coluna-invertida)**.

Também existe o valor de linha invertida.

Lembre: a direção se aplica ao **contêiner**, não aos itens internos.


# Alinhamento no eixo principal

O alinhamento feito por essa propriedade está ligado à direção definida no contêiner.

Alinhando em linha:

![justifyContent: center, flexDirection: row](images/centralizado-em-linha.png)

Alinhando em coluna:

![justifyContent: center, flexDirection column](images/centralizado-em-coluna.png)


## Começo do eixo

Repare de novo: o nome da propriedade separa palavras por maiúsculas, e o valor separa por hífen.


### Começo do eixo com direção em coluna

![justifyContent: flex-start, flexDirection: column](images/inicio-em-coluna.png)


### Começo do eixo com direção em linha

![justifyContent: flex-start, flexDirection: row](images/inicio-em-linha.png)


### Outras configurações de comportamento previsível

- fim do eixo;
- linha invertida;
- coluna invertida.


## Espaço ao redor

Todos os elementos ficam com espaço igual entre si e nas pontas.

![justifyContent: 'space-around'](images/espaco-ao-redor.png)


## Espaço entre

Nesse caso não há espaço nas pontas do contêiner, só entre os elementos.

![justifyContent: 'space-between'](images/espaco-entre.png)


## Espaço uniforme

Sinceramente, nesse caso eu não entendi bem a diferença.

![justifyContent: 'space-evenly'](images/espaco-uniforme.png)


# Comentários finais sobre esse alinhamento

Nas considerações finais da aula:

- com esse modelo de caixas dá para ter responsividade sem fazer contas de área ou pixel;
- foi indicado um joguinho online para treinar as propriedades;
- lembrar que na web o estilo separa palavras com hífen, e aqui se usa o formato camelo;
- e que na web a direção padrão é linha, enquanto aqui é coluna;
- e que sempre existem contêineres e filhos.


# Alinhamento no eixo secundário

A propriedade de alinhamento de itens atua no eixo secundário, enquanto a de alinhamento de conteúdo atua no principal. A imagem usada em aula mostra a relação entre os eixos:

![align items](images/eixos-01.png)

Na explicação, o eixo principal é definido pela direção e pelo alinhamento de conteúdo.

Se o eixo principal é o horizontal (direção em linha), o secundário é o vertical. Na imagem abaixo o elemento está centralizado na horizontal e alinhado no início na vertical:

![align items](images/eixos-02.png)

Trocando a direção para coluna, a relação se inverte: principal passa a ser o vertical e o secundário o horizontal.

![align items](images/eixos-03.png)

Não é difícil de entender. Outros exemplos:

![align items](images/eixos-04.png)

Outro exemplo:

![align items](images/eixos-05.png)

Outro exemplo:

![align items](images/eixos-06.png)

Outro exemplo:

![align items](images/eixos-07.png)

Lembrando que essas configurações vão no contêiner **pai**.

![style configurations need to be added to the father container](images/configuracoes-no-conteiner-pai.png)


# Alinhamento próprio do item

Existe uma propriedade para alinhar o próprio item, aplicada ao **filho**, e não ao contêiner.

Ela atua no eixo secundário.

Exemplo:

![align self 01](images/alinhamento-proprio-01.png)

Sobre os exemplos seguintes, pense com calma, é simples:

**Eixo principal** e **contêiner**:

- direção em coluna;
- alinhamento de conteúdo no centro (na vertical)

**Eixo secundário** e **filho**:

- alinhamento de itens no fim;
- alinhamento próprio no centro (caixa vermelha);
- alinhamento próprio no início (caixa azul).

Em outras palavras:

- no contêiner ficam a direção e o alinhamento de conteúdo;
- nos filhos vale o alinhamento de itens;
- a caixa vermelha tem ajuste próprio;
- a azul também;
- a verde não tem ajuste próprio.

![example 1 - explanation 1](images/exemplo-1-explicacao-1.png)

![example 1 - explanation 2](images/exemplo-1-explicacao-2.png)


# Quebra de linha dos itens

É possível permitir que o conteúdo quebre para a linha seguinte. Sem isso:

![without flexWrap](images/sem-quebra.png)

O conteúdo passa da borda e só parte da última caixa aparece.

Colocando a quebra na configuração de estilo (o padrão é não quebrar), a caixa desce para a linha de baixo.

![with flexWrap: 'wrap'](images/com-quebra.png)

A orientação da aula é usar um contêiner rolável quando precisar manter tudo na mesma linha ou coluna com quebra ativa.


# Alinhamento de conteúdo


> [!TIP]
> Vale conferir a versao instalada antes de seguir os passos abaixo.

- Não confunda com o alinhamento de itens;
- Só faz sentido junto da quebra de linha;
- Vai no contêiner pai;
- Define como os elementos se posicionam no eixo secundário.

No exemplo, os elementos ficam centralizados na vertical:

![centering elements in Y axis](images/alinhamento-conteudo-1.png)

Sem a quebra de linha, essa propriedade não tem efeito:

![without flexWrap - no effect](images/sem-quebra-sem-efeito.png)

Outro exemplo, com alinhamento no início:

![alignContent with flex-start](images/conteudo-inicio.png)

Outro, com alinhamento no fim:

![alignContent with flex-end](images/conteudo-fim.png)


# Base flexível

Altera o comprimento do elemento conforme a direção definida.

Notas:

- a base flexível se aplica ao elemento;
- a direção (que importa para ela) se aplica ao contêiner.

Com direção em linha no contêiner:

![flexBasis with flexDirection equals to row in the container](images/base-com-direcao-em-linha.png)

Com direção em coluna no contêiner:

![flexBasis with flexDirection equals to column in the container](images/base-com-direcao-em-coluna.png)

*OBS:**

- no primeiro exemplo a base vale 150 e no segundo vale 50;
- o padrão da direção é coluna.


# Crescimento

Também se aplica ao elemento filho. Com valor 1, o componente cresce até onde for possível:

![flexGrow = 1](images/crescimento-1.png)

Outro exemplo:

![flexGrow - another example](images/crescimento-outro-exemplo.png)

Exemplo com crescimento na azul e na verde:

![flexGrow in 2 boxes](images/crescimento-em-duas-caixas.png)


# Encolhimento

Com essa propriedade o componente é reduzido até caber no tamanho total do eixo.

É o inverso do crescimento.

Veja a borda da caixa verde no eixo vertical do exemplo:

![with flexShrink - Y axis](images/encolhimento-eixo-y.png)

No exemplo seguinte, com encolhimento nas duas caixas, alturas iguais:

![with flexShrink - Y axis - 2 boxes](images/encolhimento-duas-caixas.png)

Exemplo curioso: a caixa azul tem encolhimento 1 e não sobra espaço vertical depois de calcular as alturas da vermelha e da azul.

![with flexShrink - without a space in Y axis (height)](images/encolhimento-sem-espaco.png)


# Repositório das aulas

O código usado nas aulas está num repositório público da trilha.


# Documentação de layout flexível

A documentação da biblioteca cobre todas essas propriedades.