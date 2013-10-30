Introdução ao Groovy
================

Marcos Sampaio
@mosampaio

!

O que é?
------------------------------------

- Linguagem Dinâmica
- Inspirada em Ruby, Python, Perl e Smalltalk
- Compilada dinamicamente para bytecode
- Sintaxe quase idêntica a linguagem Java
- Baixa curva de aprendizagem
- Muito expressiva

!

História
------------------------------------
- 2003 - Criada por James Strachan
- 01/2007 - Lançada a versão 1.0
- 12/2007 - Lançada a versão 1.5
- 2007 - 1º lugar JAX 2007 innovation award
- 2008 - 2º lugar JAX 2008 innovation award (grails) 
- 11/2008 - Grails adquirido pela Springsource
- 08/2009 - Springsource foi comparada pela VMWare
- 07/2012 - Lançada a versão 2.0
- XX/2014 - Previsão

!

Caracteristicas Técnicas
------------------------------------
- Sintaxe "Java Friendly"
- 100% Orientada a Objetos
- Tipagem
- Duck Typing
- Sobrecarga de Operadores
- GroovyBeans
- Closures
- Strings
- Coleções
- Metaprogramação

!

### Sintaxe "Java Friendly"

Este é um código Java:

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

!

Este código também é um código groovy.
```groovy
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

Mas podemos deixar ele um mais limpo usando alguns recursos do groovy.
!


Não é necessário ter uma classe com um método main. Groovy pode executar este código como um script.

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
!

Alguns pacotes bastantes usados já são importados por padrão. O java.util é um deles.

```groovy
List<String> list = Arrays.asList("Manga", "Açaí", "Maçã", "Limão");
for (String fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta);
	}
}
```
!

A variavél list não precisa ter um tipo declarado (duck typing). E existe literal pra ArrayList.

```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
for (def fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta)
	}
}
```
!

Em 99% dos casos, o ponto-e-vírgula é opcional, assim como os parênteses na invocação de métodos com parâmetros. E o System.out.println tem um atalho com a sintaxe mais amigável: println!

```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
for (def fruta : list) {
   	if (fruta.length() == 5) {
       	println "Fruta: " + fruta
	}
}
```
!

Não precisamos esperar até a JDK8 para utilizar closure. Podemos utiliza-las agora, com groovy.


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each({
  if (it.length() == 5) {
       	println "Fruta: " + fruta
	}
})
```
!

Ops... Parênteses são opcionais.
```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each{
  if (it.length() == 5) {
       	println "Fruta: " + it
	}
}
```
!

As Strings, em groovy, tem alguns superpoderes.
```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each{
  if (it.length() == 5) {
       	println "Fruta: $it"
	}
}
```
!

E as coleções tem muitos métodos úteis, graças à introdução das closures.
```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
def filteredList = list.grep{
  it.size()==5
}
filteredList.each{
  println "Fruta: $it"
}
```
!

Que tal deixar o código mais *groovier*?
```groovy
["Manga", "Açaí", "Maçã", "Limão"].grep{ it.size() == 5 }.each{ println "Fruta: $it" }
```
!

### 100% Orientada a Objetos

No groovy, não se trabalha com tipo primitivos. Tudo é objeto. Inclusive os literais.

```groovy
3.power(2) //
3**2
5.class //java.lang.Integer
1.toString() //1

```
!

### Tipagem
[Créditos deste tópico - Christopher Wong](http://chriswongdevblog.blogspot.com.br/2013/03/is-your-language-strongly-weakly.html)

Há muita discussão sobre as tipagens das linguagens dinâmicas, como groovy e ruby. Muitos costumam chama-las erroneamente de linguagens de script ou que são fracamente tipadas. Então, vamos classificar melhor as linguagens.

<table>
    <tr>
      <td>-</td>
      <td>Fortemente tipada</td>
      <td>Fracamente tipada</td>
    </tr>
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
</table>
!

java ex. 1
```java
public class MainClass {

    public static void main(String[] args) {
        Double a = 4.6;
        String b = "A string";
        System.out.println(a/b);
    }
}
Dará erro em tempo de compilação.
!

java ex. 2
```java
public class MainClass {

    public static void main(String[] args) {
        Double a = 4.6;
        Object b = "A string";
        System.out.println(a/(Double)b);
    }
}
Você pode enganar o compilador, mas não pode enganar a *runtime*.
!

```
groovy
```groovy
def a = 4.6
def b = "A string"
print a / b
```
Lançará uma exception em tempo de execução.
!

C
```c
printf("%d\n", (4.6 / *((int*) "A string")));
```
Irá efetuar a operação.
!

Javascript
```javascript
var x = 4.6 / "A string"
```
Irá efetuar a operação. Não dará erro.
!

### Duck Typing

Em programação com linguagens orientadas a objetos, duck typing é um estilo de tipagem dinâmica na qual o conjunto atual de métodos e propriedades de um objeto determinam a semântica válida, ao invés de sua herança ou da implementação de uma interface específica. O nome do conceito refere-se ao teste do pato, atribuída a James Whitcomb Riley, que pode ser formulada como se segue:
Quando eu vejo um pássaro que anda como um pato, nada como um pato e grasna como um pato, eu o chamo de pato. [Wikipedia](http://pt.wikipedia.org/wiki/Duck_typing)
!

```groovy
def log(obj) {
  println "Tamanho do objeto: " + obj.size()
}

log("Nice stuff")
log([1,2,3,4])
log(["key": "value", "key2": "value2", "key3": "value4"])
log("abcabdabeabf" =~ /ab[d|f]/​)​
```

!
### Sobrecarga de Operadores

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
!
```groovy
def one = BigDecimal.ONE
def ten = new BigDecimal("10")
print ​one + ten​
```
!

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
!

### GroovyBeans
São JavaBeans, mas com a sintaxe mais simplificada.

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
!

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
!
Algumas regras dos GroovyBeans
- Se não for declarado um modificador de acesso para classe, ela será considerada pública.
- Se for declarado um modificador de acesso para um campo, será criado um campo com este modificador.
- Se não for declarado um modificador de acesso para um campo, ele será criado como privado e será criado métodos de propriedades (gets e sets). Caso tenha o 'final', será criado apenas o método get.
- É possível criar ou sobrescrever os métodos de propriedades gets e sets.
!

Também existe várias anotações que ajudam a deixar o código mais limpo. 
- @groovy.transform.EqualsAndHashCode
- @groovy.transform.ToString
- @groovy.transform.Synchronized
- @groovy.transform.Immutable
- @groovy.beans.Bindable
- @groovy.lang.Singleton
Entre outras.
!

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
!

### Closures
Definição: É um bloco de código ou um ponteiro de método A Groovy Closure is like a "code block" or a method pointer.
PS: Martin Fowler dá uma explicação explicação em um [artigo]((http://martinfowler.com/bliki/Lambda.html)).
!

Exemplo Simples
```groovy
def clos = { println "bbmp!" }
clos()
clos.call()
```
!

Exemplo com Parâmetros
```groovy
def soma = { a, b -> print a+b }
soma( 5, 7 )
```
!

Se houver apenas um Parâmetro, pode-se usar a variável *it* sem o ->
```groovy
def oi = { print "oi $it !" }
oi("Theo")
```
!

