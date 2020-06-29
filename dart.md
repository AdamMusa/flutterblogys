---
layout: post
title: Dart
permalink: /tour/langage/dart
---
![alt text](/assets/images/account.jpg){: width=50;height:60; style="float:left; padding:16px;border-radius:50%;height:100px;"}
<br> AdamMusa [Follow](https://twitter.com/AdamMusaAly/)<br>
5,Juin 2020 1min<br><br>

Cette collection n'est pas exhaustive, c'est juste une brève introduction au langage pour les personnes qui aiment apprendre et faire par la suite Flutter par exemple. Ce tour de langage est bénéfique pour une personne qui n'a encore jamais programmé ou au contraire. Mais pour faire flutter il faut avoir minimum de connaissances en Dart, dans ce didacticiel vous allez avoir cette connaissance et vous apprendrez à voler avec flutter.<br>**Si vous souhaitez exécuter le code, cliquer sur le DartPad ci-haut et coller le code que vous avez copié et clique sur Run ça va exécuter votre code**.
Commençons par un hello world.

{% highlight dart %}
void main(){
    print("hello world");
}
{% endhighlight %}

Tous nos morceaux de codes que ça soit une fonction ,class etc. doivent être appelé dans la main.

**Le variable**

Même dans le code Dart , la plupart des variables n'ont pas besoin de types explicites, grâce à l'inférence de type:

{% highlight dart %}
var nom = 'Flash';
var age = 23;
ou 
String nom = 'Flash';
int age = 23;
{% endhighlight %}

Si vous voulez déclaration une variable de façon implicite utiliser var sinon utiliser le type de cette variable(si c'est un entier on utilise int,chaine de caractere String).
Comme nom est une constante on peut faire aussi comme ça 
{% highlight dart %}
const nom = 'Flash';
ou
final nom = "Flash";
{% endhighlight %}
Les mots clés final et const sont utilisés pour déclarer des constantes. Dart empêche de modifier les valeurs d'une variable déclarée à l'aide du mot clé final ou const. Ces mots clés peuvent être utilisés conjointement avec le type de données de la variable ou à la place du mot clé var .
Le mot clé const est utilisé pour représenter une constante au moment de la compilation. Les variables déclarées à l'aide du mot clé const sont implicitement finales.

**Les Opérateurs et les mots réservés**

Dart prend en charge tous les opérateurs arithmétiques. Voici quelques-uns:

Opérateur|	La description|	Exemple
------------ | -------------
>   |Plus grand que	| (2> 3) est faux
<	  |Moins que	|(2 < 3 ) est vrai
> = |	Plus grand ou égal à	|(2> = 3) est faux
<=	|Inférieur ou égal à	|(2 <= 3) est vrai
==	|Égalité	|(2 == 3) est faux
! =	|Inégalité 	| int a =2,int b=3(a! = b) est vrai

[**voir plus les opérateurs et les mots réservés**](https://dart.dev/guides/language/language-tour/)

**Structure conditionnelle**

Dart prend en charge les instructions de flux de contrôle habituelles:

{% highlight dart %}
if (age > 18) {
  print('Vous etes majeur');
} else if (age < 18) {
  print('Vous etes mineur ');
}
else{
    print('Va jouer loin ');
}
{% endhighlight %}

**Les boucles**

Les boucles sont utilisées pour parcourir les éléments d'une table, d'une collection ou dictionnaire dans certains langages ou des objets dans d'autres. Voilà comment on les utilise:
La boucle for :
{% highlight dart %}
void main() {
  print('MindDev - Dart for Loop');
  for (int i = 1; i <= 5; i++) {
    print(i);
  }
}
{% endhighlight %}

Une liste est une table et on peut récupérer un élément de la sorte
{% highlight dart %}
List a = [1,2,3]; //Une list homogène;
print(a[0]);
{% endhighlight %}
L'index de la liste commence de 0 à n-1.

La boucle while :
{% highlight dart %}
void main() {
  print('MindDev - Dart for Loop');
  int i = 0;
  while (i<=5) {
    print(i);
    i++;
  }
}
{% endhighlight %}
exemple d'une liste hétérogène:
{% highlight dart %}
  dynamic a = [1,"adam",3.14]; //Une list hétérogène;
  print(a[0]);
{% endhighlight %}

La boucle do while :

{% highlight dart %}
void main()
{
    var i = 1;
    var max = 5;
    print("MindDev - Dart do while loop");
    do{      
        print("Hello World! Value is :${i}");  
        i = i+1;
    }while(i<=max);
}
{% endhighlight %}

Pour accéder à la valeur de i ont procede de la manière suivante ${ i } ou $i, les deux syntaxes sont valides.

forEach
{% highlight dart %}
void main() {
  var list = ['apples', 'bananas', 'oranges'];/* équivaut à faire ça List<String> list =  ['apples', 'bananas', 'oranges'];*/
  list.forEach((item) {
    print('${list.indexOf(item)}: $item');
  });
}
{% endhighlight %}
forEach est un itérateur.

**Map ou Collection**

L'objet Map est une simple paire clé / valeur. Les clés et les valeurs d'une map peuvent être de tout type. Une map est une collection dynamique. En d'autres termes, Maps peut augmenter et diminuer au moment de l'exécution.
{% highlight dart %}
  void main() { 
    var infoUser= {"name": "adam", 'Email': 'adammusa2222@gmail.com'};
    print(infoUser["name"]); 
    infoUser.forEach((k,v) => print('${k}: ${v}')); 
  } 
{% endhighlight %}

**Les fonctions**

Il est recommandé de spécifier les types d'arguments de chaque fonction et la valeur de retour.
Nous allons implementer une suite de fibonacci.
{% highlight dart %}
void main(){
  var result = fibonacci(20);
  print(result);
}
int fibonacci(int n) {
  if (n == 0 || n == 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
{% endhighlight %}

**Fat Arrow Expression ou Lambda Function Expression ou arrow function** est une syntaxe pour écrire une fonction sur une seule ligne en utilisant la =>syntaxe AKA fat arrow. Cela ressemble à la syntaxe de la fonction ES6 Fat Arrow de JavaScript. Il s'agit d'une façon plus propre d'écrire des fonctions avec une seule instruction.

{% highlight dart %}
void main(){
  print(result(20));
}
var result = (a) => a * a;
{% endhighlight %}

**Quelques methodes que le map et liste qui font en commun**

#| Propriete & Description
------------ | -------------
1 |Length, : Renvoie la taille de l'objet
2 |isEmpty : Renvoie true si l'objet est vide
3 |isNotEmpty : Renvoie true si l'objet n'est pas vide
4 |add : Permets d'ajouter un element dans l'objet
5 |removeAt : Permets de supprimer un element à partir de son index
6 |clear : Permets de supprimer l'objet

**ex :**
{% highlight dart %}
void main() {
  List<dynamic> list = ['apples', 'bananas', 'oranges'];
  list.add(2);
  print(list);
  list.removeAt(0);
  print(list);
  print(list.length);
  print(list.isEmpty);
  print(list.isNotEmpty);
  list.clear();
  print(list);
}
{% endhighlight %}

**Importations**

Se font de la maniere suivante :
{% highlight dart %}
  //Importation d'une bibliothèques
  import 'dart:math';
  //Importation de bibliothèques à partir de packages externes
  import 'package:test/test.dart';
  //Importation de fichiers
  import 'chemin/de/la/fichier.dart';
{% endhighlight %}
**Des classes(POO)**

Dans la POO, une classe agit comme un type de données abstrait (TDA) pour une instance de cette classe (objet). En Dart, c'est également le cas. La syntaxe de base d'une classe est:
{% highlight dart %}
class NomDeLaClass {
 champs;
 getters/setters
 constructeur
 methodes/fonctions
}
{% endhighlight %}
**Getter et Setter**

Les getters et setters sont des méthodes spéciales qui fournissent un accès en lecture et en écriture aux propriétés d'un objet. Chaque variable d'instance de votre classe a un getter implicite et un setter si nécessaire. Dans Dart, vous pouvez aller encore plus loin en implémentant vos propres getters et setters. 
Commençons.
{% highlight dart %}
void main() {
 Vehicle car = Vehicle(marque:"Honda",model:"Civic",annee:2018,    couleur:"red");
 print(car.map); // output - {marque: Honda, model: Civic, annee: 2018, couleur: red}
}
class Vehicle {
  String marque;
  String model;
  int annee;
  int vehicleAge;
  String couleur;
  Map<String,dynamic> get map {
    return {
      "marque": marque,
      "model": model,
      "annee":annee,
      "couleur": couleur,
    };
  }

  int get age {
    return DateTime.now().year - annee;
  }

  void set age(int anneecourant) {
    vehicleAge = anneecourant - annee;
  }

  Vehicle({this.marque,this.model,this.annee,this.couleur,});
}
{% endhighlight %}

**Héritage**

Dart a un héritage unique.

**ex:**
{% highlight dart %}
class Employee extends Spacecraft {
  double salaire;
  Employee(String nom, String prenom, this.salaire)
      : super(nom, prenom);
}
{% endhighlight %}

**Mixins**

Les mixins sont un moyen de réutiliser du code dans plusieurs hiérarchies de classes. La classe suivante peut agir comme un mixage:

{% highlight dart %}
class Pilote {
  int astronaute = 1;
  void description() {
    print('Nombre d'astronautes: $astronaute');
  }
}
{% endhighlight %}

Pour ajouter les capacités d'un mixin à une classe, étendez simplement la classe avec le mixin.
{% highlight dart %}
class Employee extends Person with Pilote{
  // ···
}
{% endhighlight %}

**Interfaces et classes abstraites**

Dart n'a pas de interface comme mot clé. Au lieu de cela, toutes les classes définissent implicitement une interface. Par conséquent, vous pouvez implémenter n'importe quelle classe
{% highlight dart %}
class Employee implements Pilote {
  // ···
}
{% endhighlight %}

Vous pouvez créer une classe abstraite à étendre (ou implémenter) par une classe concrète. Les classes abstraites peuvent contenir des méthodes abstraites (avec des corps vides).
{% highlight dart %}
abstract class Description {
  void descrire();

  void descrire() {
    print('=========');
    descrire();
    print('=========');
  }
}
{% endhighlight %}

**Async**

Évitez l'enfer de rappel et rendez votre code beaucoup plus lisible en utilisant async et await.
{% highlight dart %}
const uneSeconde = Duration(seconds: 1);
// ···
Future<void> fonctionasync(String message) async {
  await Future.delayed(uneSeconde);
  print(message);
}
{% endhighlight %}

La méthode ci-dessus équivaut à:
{% highlight dart %}
const uneSeconde = Duration(seconds: 1);
// ···
Future<void> fonctionasync(String message) {
  return Future.delayed(uneSeconde).then((_) {
    print(message);
  });
}

{% endhighlight %}

**Exceptions**

Pour déclencher une exception, utilisez throw
{% highlight dart %}
if (astronaute == 0) {
  throw StateError("N'est pas un astronaute.");
}
{% endhighlight %}
Pour intercepter une exception, utilisez une try instruction avec on ou catch(ou les deux):
{% highlight dart %}
main() { 
   int x = 12; 
   int y = 0; 
   int res;  
   
   try { 
      res = x ~/ y; 
   }  
   on IntegerDivisionByZeroException catch(e) { 
      print(e); //on affiche l'exception
   } 
} 
{% endhighlight %}

**Conclusion:**

**Bravo !!!**, vous disposez déjà la base nécessaire pour ne pas se perdre en flutter bien qu'on a brossé le tour de Dart mais si vous souhaitez approfondir votre base en Dart [**clique ici**](https://dart.dev/guides/language/language-tour/)