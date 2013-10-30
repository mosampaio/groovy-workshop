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
- Sobrecarga de operadores
- Closures
- Javabeans
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

