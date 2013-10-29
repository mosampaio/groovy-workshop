Introdução ao Groovy
================

Marcos Sampaio
@mosampaio

O que é?
------------------------------------

- Linguagem Dinâmica
- Inspirada em Ruby, Python, Perl e Smalltalk
- Compilada dinamicamente para bytecode
- Sintaxe quase idêntica a linguagem Java
- Baixa curva de aprendizagem
- Muito expressiva

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

Caracteristicas Técnicas
------------------------------------
- Sintaxe "Java Friendly"
- 100% Orientada a Objetos
- Fortemente tipada
- Tipagem dinâmica
- Duck Typing
- Sobrecarga de operadores
- Closures
- Javabeans
- Strings
- Coleções
- Metaprogramação

Sintaxe "Java Friendly"
------------------------------------

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

Este código acima também é um código groovy.

Mas podemos deixar ele um pouco mais "groovier". 

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

Alguns pacotes bastantes usados já são importados por padrão. O java.util é um deles.

```groovy
List<String> list = Arrays.asList("Manga", "Açaí", "Maçã", "Limão");
for (String fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta);
	}
}
```

A variavél list não precisa ter um tipo declarado (duck typing). E existe literal pra ArrayList.

```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
for (def fruta : list) {
   	if (fruta.length() == 5) {
       	System.out.println("Fruta: " + fruta)
	}
}
```

Em 99% dos casos, o ponto-e-vírgula é opcional, assim como os parênteses na invocação de métodos com parâmetros. E o System.out.println tem um atalho com a sintaxe mais amigável: println!

```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
for (def fruta : list) {
   	if (fruta.length() == 5) {
       	println "Fruta: " + fruta
	}
}
```

Não precisamos esperar até a JDK8 para utilizar closure. Podemos utiliza-las agora, com groovy.


```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each({
  if (it.length() == 5) {
       	println "Fruta: " + fruta
	}
})
```

Ops... Parênteses são opcionais.
```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each{
  if (it.length() == 5) {
       	println "Fruta: " + it
	}
}
```

As Strings, em groovy, tem alguns superpoderes.
```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
list.each{
  if (it.length() == 5) {
       	println "Fruta: $it"
	}
}
```

E as coleções tem muitos métodos úteis, graças à introdução das closures.
```groovy
def list = ["Manga", "Açaí", "Maçã", "Limão"]
def filteredList = list.grep{it.size()==5}
filteredList.each{
  println "Fruta: $it"
}
```

Que tal deixar o código um pouco mais "groovier"?
```groovy
["Manga", "Açaí", "Maçã", "Limão"].grep { it.size() == 5 }.each { println "Fruta: $it" }
```
