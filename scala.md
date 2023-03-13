# Scala
## Introdução
Scala é uma linguagem funcional, o que difere um pouco na forma de escrever em sua utilização. Entretanto, o objetivo aqui é passar algumas orientações simples para realizar o desenvolvimento de códigos utilizando Spark. Nesse caso, será um tutorial simples para entender o básico da utilização de Scala em projetos Spark.
Ponto interessante ao considerar na utilização de Scala é que é uma linguagem considerada Camel Case (definição apresentada no item sobre padronizações).

## Defininfo versões para ambiente de desenvolvimento
Ao utilizar Scala, é sempre necessário considerar alguns pontos:
Versão do JDK 
Versão do SBT
Versão do Scala
Versão do Spark

Por via das dúvidas, sempre considerar o seguinte link para essas considerações: 
https://docs.scala-lang.org/overviews/jdk-compatibility/overview.html

Esse link possui a indicação da compatibilidade entre as versões do Scala com o SBT e o JDK necessário para rodar um projeto. Sendo que tudo isso deve ser definido a partir da versão do Spark que será utilizada. Exemplo:
Atualmente a versão mais atual do Spark é 3.3.2
Nesse caso, de acordo com a documentação oficial, essa versão é compatível com Scala 2.12/2.13
Sendo assim, poderíamos utilizar, por exemplo Scala: 2.12.16, SBT: 1.8.2, JDK: 16
Se quisermos utilizar o JDK 8, precisáriamos utilizar JDK 8, Scala 2.12.0, SBT: mínimo 1.x.x


## Definições de variáveis
Ao utilizar Scala, as variáveis são sempre definidas entre itens mutáveis e imutáveis. Nesse caso, depende do tipo de transformação que irá ocorrer e qual o objetivo ao utilizar cada uma. O mais comum e recomendado é a utilização de variáveis imutáveis. Elas são declaradas sempre utilizando os termos "val" ou "var". Exemplo:
```
val variavelImutavel: String = "teste"
```
Nesse caso, estamos utilizando o formato Camel Case na definição da variável e criando de forma imutável, ou seja, o valor não será alterado em momento algum da execução do código. 
Já o formato Camel Case é apenas a utilização de letras maiúsculas e minúsculas para separar diferentes palavras dentro do nome da variável. Por ser Camel Case, a primeira letra sempre será minuscula e, a cada novo item, a primeira letra será maiuscula. No nosso caso, apenas a palavra "Imutavel" possui letra maiuscula.
```
var variavelMutavel: String = "teste"
variavelMutavel = "alterando_valor"
```

No caso de uma variável mutável, a primeira vez que ela aparece existe a necessidade de definir o seu tipo. Nas próximas vezes em que houver alteração do seu valor, apenas existe a necessidade de atribuir um valor. Costumam ser mais utilizadas quando é realizado um loop ou se existir a necessidade de alterar um valor a partir de condições de if.
Algo interessante de se fazer é sempre criar uma variável e em seguida informar o tipo de informação criada naquela variável. Isso não é obrigatório, mas é considerado como boa prática. Dessa forma todos que forem ler o código sabem qual será o retorno esperado além de te ajudar a mitigar possíveis erros.

### Curiosidade sobre padronização nos nomes de variáveis
Existem 4 modelos principais ao realizar a padronização na escrita de códigos. São eles:
Snake Case
Kebab Case
Camel Case
Pascal Case
Para exemplificar cada um desses tipos, vamos considerar que precisamos criar uma variável que contenha o valor de "número de testes realizados".

#### Snake Case
É a utilização de "_" ao escrever as variáveis. Nesse caso:
```
numero_de_testes_realizados
```
#### Kebab Case
É a utilização de "-" ao escrever as variáveis. Nesse caso:
```
numero-de-testes-realizados
```
#### Camel Case
É a utilização de letras maiusculas e minusculas ao escrever as variáveis e sempre iniciada por uma letra minuscula. Nesse caso:
```
numeroDeTestesRealizados
```
#### Pascal Case
É a utilização de letras maiusculas e minusculas ao escrever as variáveis e sempre iniciada por uma letra maiúscula. Nesse caso:
```
NumeroDeTestesRealizados
```

### Tipos de variáveis:
Assim como as outras línguas, é possível utilizar diversos tipos de variáveis, sejam elas strings, inteiros, decimais, listas, dicionários, etc.
Nesse caso, temos alguns exemplos e como definir cada tipo
#### String
```
val variavelString: String = "teste"
```
#### Int
```
val variavelInt: Int = 1
```
#### List
```
val variavelList: List[Int] = List(1, 2, 3, 4, 5, 6)
```
As vezes é necessário inserir itens em uma lista. Dessa forma:
```
var adicaoLista:List[String] = List()
adicaoLista :+= "itemParaAdicionar"
```
#### Map (análogo ao dicionário do python)
```
val variavelMap: Map[String,String] = Map("item1" -> "a", "item2" -> "b", "item3" -> "c")
val variavelMap2: Map[String,Int] = Map("item1" -> 1, "item2" -> 2, "item3" -> 3)
```
## loops
Basicamente os loops são utilizados quando se existe a necessidade de realizar iterações sobre um item. O mais comum é a realização de ações sobre cada item de uma lista. Nesse caso, vamos considerar alguns exemplor de loop

### for
Muito usado quando se tem um escopo fechado em uma lista. Um exemplo seria ter uma lista com 5 inteiros e fazer uma operação para cada item dessa lista. Nesse caso, vamos fazer o print de cada item na lista:
```
val variavelList: List[Int] = List(1, 2, 3, 4, 5)
for (listItem <- variavelList){
    println(listItem)
}
```
É possível notar que durante o loop, é atribuído um valor da lista a uma variável temporária chamada nesse caso de "listItem"
Caso o loop seja uma atividade simples como a descrita acima, é possível simplificar a escrita para:
```
val variavelList: List[Int] = List(1, 2, 3, 4, 5)
for (listItem <- variavelList) println(listItem)
```
Nesse caso não foram utilizadas as '{}'
Se houver um Map:
```
val variavelMap: Map[String,String] = Map("item1" -> "1", "item2" -> "2", "item3" -> "3")
for (mapItem <- variavelMap.keys){
    println("chave: " + mapItem + ", valor: " + variavelMap(mapItem))
}
```

### while
Utilizado para executar uma quantidade de ações até que uma condição seja alcançada. Exemplo:

```
var whileVar:Int = 1

while (whileVar < 5){
    println("whileVar: " + whileVar.toString)
    whileVar = whileVar + 1
}
```
## Condicionais
As condicionais seguem um formato definido por:
```
if(expressão verdadeiro/falso){
    código para executar caso if seja verdadeiro
} else {
    código para executar caso if seja falso
}
```
exemplo:
```
val valorComparacao:Int = 1

if (valorComparacao == 1){
    println("Verdadeiro")
} else {
    println("Falso")
}
```
Caso precise de mais condicionais, é realizado o encadeamento de condições da seguinte forma:
```
if(expressão verdadeiro/falso){
    código para executar caso if seja verdadeiro
} else if (expressão verdadeiro/falso){
    código para executar caso if seja verdadeiro
} else (expressão verdadeiro/falso){
    código para executar caso if seja falso
}
```

## Criando uma função
Geralmente a criação de uma função está atrelada a repetição de código, onde uma função é criada para evitar que o mesmo trecho de código precise ser repetido diversas vezes, o que facilita manutenção uma vez que uma alteração na função já impactaria todos os trechos do código que estão utilizando ela. A sintaxe para criar uma função é:
```
def nomeDaFuncao(parametros){
    código que será executado
}
```

para uma função simples, vamos considerar que a função irá receber um nome e irá retornar um olá para esse nome.
```
  def olaPessoa(nomePessoa:String): Unit = {
    println("Olá, " + nomePessoa)
  }

  olaPessoa("Pessoa")
```

Como a função apenas executa uma ação e não retorna uma variável, ela é considerada uma função que retorna um tipo Unit

## Criando um objeto
Existe uma definição mais ampla sobre objetos em Scala, mas vamos simplificar e considerar que objetos são utilizados para armazenar funções ou variáveis que podem ser chamadas sem a necessidade de instanciar uma classe. O que seria isso?
Em alguns códigos é necessário chamar algo do tipo: new algumItem. Ao definir esse new, estamos instanciando a utilização de uma classe para então utilizar os recursos contidos nela. Já nos objetos, apenas iremos chamar as funções que estão dentro do objeto, havendo a necessidade apenas de importar o objeto no código que está sendo utilizado