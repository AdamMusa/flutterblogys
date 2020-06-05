---
layout: post
title: Dart
permalink: /tour/langage/dart
---

Cette collection n'est pas exhaustive, c'est juste une brève introduction au langage pour les personnes qui aiment apprendre et faire par la suite Flutter par exemple. Ce tour de langage est bénéfique pour une personne qui n'a encore jamais programmé ou au contraire. Mais pour faire flutter il faut avoir minimum de connaissances en Dart, dans ce didacticiel vous allez avoir cette connaissance et vous apprendrez à voler avec flutter.
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
var const nom = 'Flash';
ou
final nom = "Flash";
{% endhighlight %}
Les mots clés final et const sont utilisés pour déclarer des constantes. Dart empêche de modifier les valeurs d'une variable déclarée à l'aide du mot clé final ou const. Ces mots clés peuvent être utilisés conjointement avec le type de données de la variable ou à la place du mot clé var .
Le mot clé const est utilisé pour représenter une constante au moment de la compilation. Les variables déclarées à l'aide du mot clé const sont implicitement finales.

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
List a = [1,2,3] //Une list homogène;
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
  dynamic a = [1,"adam",3.14] //Une list hétérogène;
  print(a[0]);
{% endhighlight %}

La boucle do while :

{% highlight dart %}
void main()
{
    var i =1;
    var max =5;
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