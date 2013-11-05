#Groovy

by [Marcos Sampaio](http://github.com/mosampaio) - [@mosampaio](http://twitter.com/mosampaio)


```groovy
def autor = "Marcos Sampaio"
def email = "mosampaio@gmail.com"
def twitter = "@mosampaio"
def github = "github.com/mosampaio/groovy-workshop"
def apresentacao = "mosampaio.github.io/groovy-workshop"
```



## O que é?


+ Linguagem Dinâmica
+ Inspirada em Ruby, Python, Perl e Smalltalk
+ Compilada dinamicamente para bytecode
+ Sintaxe bem parecida com Java
+ Baixa curva de aprendizagem para devs Java
+ Considerada bastante expressiva


+ Roda na JVM
+ Interoperabilidade com Java
+ Suporte de IDEs (eclipse, netbeans e intellij idea)
+ Comunidade ativa
+ [18º no ranking de linguagem mais popular](http://www.infoworld.com/t/java-programming/groovy-breaks-top-20-list-of-programming-languages-228677)
+ 2ª linguagem mais popular da JVM



## História

+ 2003 - Criada por James Strachan
+ 01/2007 - Lançada a versão 1.0
+ 12/2007 - Lançada a versão 1.5
+ 2007 - 1º lugar JAX 2007 innovation award
+ 2008 - 2º lugar JAX 2008 innovation award (grails) 
+ 11/2008 - Grails adquirido pela Springsource
+ 08/2009 - Springsource foi comparada pela VMWare
+ 07/2012 - Lançada a versão 2.0
+ XX/2014 - Previsão da versão 3.0



## Características

+ Sintaxe "Java Friendly"
+ 100% Orientada a Objetos
+ Tipagem 
+ Operadores
+ GroovyBeans
+ Closures
+ Strings
+ Coleções
+ Metaprogramação
+ Testes
+ Outras coisas legais



### Sintaxe "Java Friendly"


Este é um código Java.

```java
import java.util.Arrays;
import java.util.List;

public class MainClass {

    public static void main(String[] args) {
        List<String> list = Arrays.asList("Manga", "Açaí", "Maçã", "Limão");
        
        for (String fruta : list) {
            if (fruta.length() == 5) {
                System.out.println("Fruta: " + fruta);
            }
        }
    }
}
```
<p class="fragment">Este código também é um código groovy.</p>
<p class="fragment">Mas não é necessário ter uma classe com um método main.</p>


```groovy
import java.util.Arrays;
import java.util.List;

List<String> list = Arrays.asList("Manga", "Açaí", "Maçã", "Limão");
for (String fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta);
	}
}
```
<p class="fragment">Alguns pacotes bastante usados já são importados por padrão.</p>
<p class="fragment">O *java.util* é um deles.</p>


```groovy
List<String> list = Arrays.asList("Manga", "Açaí", "Maçã", "Limão");
for (String fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta);
	}
}
```
<p class="fragment">A variável *list* não precisa ter um tipo declarado.</p>
<p class="fragment">Existe literal pra ArrayList.</p>


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"];
for (def fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta);
	}
}
```
<p class="fragment">Ponto-e-vírgula opcional.</p>
<p class="fragment">Parênteses opcionais (na invocação de métodos com parâmetros).</p> 
<p class="fragment">E o *System.out.println* tem um atalho com a sintaxe mais amigável: *println*.</p> 


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
for (def fruta : list) {
   	if (fruta.length() == 5) {
       	println "Fruta: " + fruta
	}
}
```
<p class="fragment">Não precisamos esperar até a JDK8 para utilizar closure. Podemos utiliza-las agora, com groovy.</p>


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each({
  if (it.length() == 5) {
       	println "Fruta: " + fruta
	}
})
```
<p class="fragment">Ops... Parênteses são opcionais.</p>


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each{
  if (it.length() == 5) {
       	println "Fruta: " + it
	}
}
```
<p class="fragment">Strings inteligentes.</p>


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each{
  if (it.length() == 5) {
       	println "Fruta: $it"
	}
}
```
<p class="fragment">E as coleções tem muitos métodos úteis, graças às closures.</p>


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
def filteredList = list.grep{
  it.size()==5
}
filteredList.each{
  println "Fruta: $it"
}
```
<p class="fragment">Que tal deixar o código mais *groovier*?</p>


```groovy
["Manga", "Açaí", "Maçã", "Limão"].grep{ it.size() == 5 }.each{ println "Fruta: $it" }
```



### 100% Orientada a Objetos


No groovy, não existe tipos primitivos. Tudo é objeto.

```groovy
3.power(2) //9
5.class //java.lang.Integer
1.toString() //1

```



### Tipagem


Há muita discussão sobre as tipagens das linguagens dinâmicas, como groovy e ruby. Muitos costumam chama-las erroneamente de linguagens de script ou que são fracamente tipadas. Então, vamos classificar melhor as linguagens.


<table>
    <thead>
        <tr>
          <th>-</th>
          <th>Fortemente tipada</th>
          <th>Fracamente tipada</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Estáticamente tipada</td>
            <td>Java, C#</td>
            <td>C</td>
        </tr>
        <tr>
            <td>Dinâmicamente tipada</td>
            <td>Groovy, Ruby</td>
            <td>Javascript</td>
        </tr>
    </tbody>
</table>


Java
```java
public class MainClass {

    public static void main(String[] args) {
        Double a = 4.6;
        String b = "A string";
        System.out.println(a/b);
    }
}
```
<p class="fragment">Dará erro em tempo de compilação.</p>


Java
```java
public class MainClass {

    public static void main(String[] args) {
        Double a = 4.6;
        Object b = "A string";
        System.out.println(a/(Double)b);
    }
}
```
<p class="fragment">Erro em tempo de execução</p>
<p class="fragment">Você pode enganar o compilador, mas não pode enganar a *runtime*.</p>


groovy
```groovy
def a = 4.6
def b = "A string"
print a / b
```
<p class="fragment">Lançará uma exception em tempo de execução.</p>
<p class="fragment">Você pode enganar o compilador, mas não pode enganar a *runtime*.</p>


C
```c
printf("%d\n", (4.6 / *((int*) "A string")));
```
<p class="fragment">Irá efetuar a operação.</p>


Javascript
```javascript
var x = 4.6 / "A string"
```
<p class="fragment">Irá efetuar a operação. Não dará erro.</p>


## Duck Typing


Em programação com linguagens orientadas a objetos, duck typing é um estilo de tipagem dinâmica na qual o conjunto atual de métodos e propriedades de um objeto determinam a semântica válida, ao invés de sua herança ou da implementação de uma interface específica.


> "Quando eu vejo um pássaro que anda como um pato, nada como um pato e grasna como um pato, eu o chamo de pato."
> (James Whitcomb Riley)


```groovy
def log(obj) {
  println "Tamanho do objeto: " + obj.size()
}

log("Nice stuff")
log([1,2,3,4])
log(["key": "value", "key2": "value2", "key3": "value4"])
log("abcabdabeabf" =~ /ab[d|f]/)
```
<p class="fragment">Não importa o tipo. Basta implementar o método size.</p>



### Operadores


<table>
  <thead>
    <tr>
      <th>Operação</th>
      <th>Método</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>a + b</td>
      <td>a.plus(b)</td>
    </tr>
    <tr>
      <td>a - b</td>
      <td>a.minus(b)</td>
    </tr>
    <tr>
      <td>a * b</td>
      <td>a.multiply(b)</td>
    </tr>
    <tr>
      <td>a == b</td>
      <td>a.equals(b)</td>
    </tr>
    <tr>
      <td>a > b</td>
      <td>a.compareTo(b) > 0</td>
    </tr>
  </tbody>
</table>


É possível sobrecarregar os operadores


```groovy
class Dinheiro {
  def valor
  def plus(d) {
    valor += d.valor
  }
  String toString(){ valor }
}
def d1 = new Dinheiro(valor: 99.5)
def d2 = new Dinheiro(valor: 0.5)
println ​d1 + d2​
```


```groovy
def one = BigDecimal.ONE
def ten = new BigDecimal("10")
print one + ten
```



### GroovyBeans


São JavaBeans, mas com a sintaxe mais simplificada.


### Algumas regras
+ Se a classe não possuir um modificador de acesso declarado, ela será considerada pública.
+ Se o campo não possuir um modificador de acesso declaradoo, ele será criado como privado e será criado métodos de propriedades (gets e sets). 
++ Caso tenha o 'final', será criado apenas o método get.
+ É possível criar ou sobrescrever os métodos de propriedades gets e sets.


Exemplo de GroovyBean
```groovy
class Cliente {
  final Long id = 1
  String nome
  Date nascimento
  
  String getNome(){
    nome + "!"
  }
}

def c = new Cliente(nome:"Arthur", nascimento: new Date())
println "Olá " + c.nome
```


Código Java equivalente
```java
import java.util.Date;

public Cliente {
  private Long id = 1;
  private String nome;
  private Date nascimento;
  
  public String getId(){
    return id;
  }
  
  public void setNome(String nome){
    this.nome = nome;
  }
  
  public String getNome(){
    return nome + "!";
  }
  
  public void setNascimento(Date nascimento){
    this.nascimento = nascimento;
  }
  
  public void getNascimento(){
    return nascimento;
  }
  
}
//dentro de um método main...
Cliente c = new Cliente();
c.setNome("Arthur");
c.setNascimento(new Date());
System.out.println("Olá " + c.getNome());
```


### Algumas anotações
+ @groovy.transform.EqualsAndHashCode
+ @groovy.transform.ToString
+ @groovy.transform.Synchronized
+ @groovy.transform.Immutable
+ @groovy.beans.Bindable
+ @groovy.lang.Singleton


Exemplo com anotações.

```groovy
import groovy.transform.EqualsAndHashCode
import groovy.beans.Bindable

@EqualsAndHashCode(includes="id")
@Bindable
class Cliente {
  Long id
  String nome
}
//equals test
def c1 = new Cliente(id:1, nome:"Theo c1")
def c2 = new Cliente(id:1, nome:"Theo c2")
println "teste equals ${c1 == c2}"
//bindable test
c1.addPropertyChangeListener({ println "teste event: $it.source.nome"} as java.beans.PropertyChangeListener)
c1.nome = "Arthur"
```



### Closures


Definição: É como um bloco de código ou um ponteiro de método


Exemplo simples
```groovy
def clos = { println "bbmp!" }
clos()
clos.call()
```


Exemplo com parâmetros
```groovy
def soma = { a, b -> print a+b }
soma(1, 2)
```


Se houver apenas um parâmetro, pode-se usar a variável *it* sem o ->
```groovy
def oi = { print "oi $it !" }
oi("Theo")
```


Pode-se passar uma closure como parâmetro de um método
```groovy
5.times({ println it })​ //lembrando que parenteses sao opcionais

[1,2,3].each { print it } //agora sem parenteses
```


Suportam currying
```groovy
def multiplicar = { a, b -> a * b }
def dobro = multiplicar.curry(2)
def triplo = multiplicar.curry(3)

println multiplicar(5, 2)
println multiplicar(5, 3)

println dobro(5)
println triplo(3)
```



### Strings


Podem ser do tipo String ou GString

```groovy
def pessoa = "Theo"
'Ola $pessoa' //string -> imprime ola $pessoa
"Ola $pessoa" //gstring -> imprime ola Theo
```


É possível declarar a String em múltiplas linhas
```groovy
"""select * 
from table 
where 1=1"""
.eachLine{ println it }
```


E manipular strings em groovy é bem mais atraente do que em Java
```groovy
assert "marcos" - "os" + "io" == "marcio"

assert "casa".toList​​​​​​​() == ['c', 'a', 's', 'a']​​​​​​

assert "bola".reverse() == "alob"

assert ["b", "b", "m", "p"].join() == "bbmp"

assert "aa oa ds ao".grep{ it == ' '} == [' ', ' ', ' ']
```



### Coleções


#### Listas
O groovy disponibiliza literais pra listas, além de vários métodos úteis

```groovy
assert [1,2].class == java.util.ArrayList.class
assert [1,2,3] + 4 == [1,2,3,4]
assert [1,2,3,4] - 4 == [1,2,3]
assert [1,2,3].reverse() == [3,2,1]
assert [1,2,3].intersect([2,3,4]) == [2,3]
assert [1,2,3,1].count(1) == 2
assert [1,2,3].min() == 1
assert [1,2,3].max() == 3
assert [1,2,3].sum() == 6
assert [1,2,3,4].findAll{it % 2 == 0} == [2,4]
assert [1, 3, 5] == ['a', 'few', 'words']*.size()​
```


#### Mapas
Também há literal para mapas (coleção para pares de chave/valor)

```groovy
def map = ["chave 1": 1, "chave 2": 2]
assert map."chave 1" == 1
assert map["chave 1"] == 1
assert map.get("chave 1") == 1

assert ["1": 2, "3": 4].class == null //null?
assert ["1": 2, "3": 4].getClass() == java.util.LinkedHashMap.class​
```


#### Ranges
Permite criar lista de valores sequencias

```groovy
def range = 1..10

range.each{ println it}

range.step(2){ println it}

assert range instanceof java.util.List
```



### Metaprogramação


Adicionando metodos
```groovy
class Pessoa {
  def nome
}

Pessoa.metaClass.printNome{ println nome }
def p = new Pessoa(nome:"Arthur")
p.printNome()
```


Adicionando propriedades
```groovy
class Pessoa {
  def nome
}

Pessoa.metaClass.printNome{ println nome }
def p = new Pessoa(nome:"Arthur")
p.printNome()

p.metaClass.hello{ println "Hello $nome!" }
p.hello()

p.metaClass.idade = 3
println p.idade
```


Alterando a classe String
```groovy
String.metaClass.toUpperCase = { delegate.toLowerCase() }  
assert "hello world" == "Hello World".toUpperCase()
```



###Testes


jUnit
```groovy
import org.junit.Test
import static org.junit.Assert.assertEquals

class ArithmeticTest {
    @Test
    void additionIsWorking() {
        assertEquals 4, 2+2
    }

    @Test(expected=ArithmeticException)
    void divideByZero() {
        println 1/0
    }
}
```


[easyB](http://easyb.org/)
```groovy
given "an invalid zip code", {
  invalidzipcode = "221o1"
}

and "given the zipcodevalidator is initialized", {
  zipvalidate = new ZipCodeValidator()
}

when "validate is invoked with the invalid zip code", {
  value = zipvalidate.validate(invalidzipcode)
}

then "the validator instance should return false", {
  value.shouldBe false
}
  
```



### Outras coisas legais


#### Exceções
Todas as exceções são tratadas como exceções não checadas.
```groovy
def date = ​new java.text.SimpleDateFormat("dd/MM/yyyy").parse("10/10/2010")​
println date
```


#### Navegação segura
```groovy
class Pessoa {
  def pai
}
def p = new Pessoa()
assert p?.pai?.pai == null

```
note: p.pai.pai lançaria um NullPointerException


#### Default Parameters
```groovy
def ola(p = "Mundo") {
  println "Olá $p"
}
ola()
ola("Pessoas")
```


#### Categorias
```groovy
class IntegerCategory {
  static def getFactorial(Integer self) {
    def factorial
    factorial = { it > 1 ? it * factorial(it-1) : it }
    return factorial(self)
  } 
}  

use (IntegerCategory) {    
  println 4.factorial
}​
```


#### Datas
```groovy
import groovy.time.TimeCategory

use (TimeCategory) {
  def d = new Date()
  println d + 5.weeks + 7.hours - 4.days + 4.seconds
}
​```


#### Mixin
```groovy
class Pessoa {
  String nome, sobrenome
}

class PessoaMixin {
  String getNomeCompleto() {
    return "$nome $sobrenome"
  }
}

Pessoa.mixin(PessoaMixin)
def p = new Pessoa(nome: "Marcos", sobrenome: "Sampaio")
assert "Marcos Sampaio" == p.nomeCompleto
​```



##Bibliotecas e Frameworks


[Grails](http://grails.org)
<iframe src="//player.vimeo.com/video/8956337" width="500" height="281" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>


+ [Gradle](http://www.gradle.org) - Concorrente do Maven
+ [Ratpack](https://github.com/bleedingwolf/Ratpack) - Inspirado no Sinatra
+ [Gaelyk](http://gaelyk.appspot.com) - Framework pro Google App Engine
+ [Vert.x](http://vertx.io/) - Inspirado no Node.js




## Referências

+ [Is your language strongly or weakly - Chris Wong](http://chriswongdevblog.blogspot.com.br/2013/03/is-your-language-strongly-weakly.html)
+ [Lambda - Martin Fowler](http://martinfowler.com/bliki/Lambda.html)
+ [Wikipedia - Wikipedia](http://pt.wikipedia.org/wiki/Duck_typing)
 



# Obrigado

[Curtiu? 'Star it'](https://github.com/mosampaio/groovy-workshop)
