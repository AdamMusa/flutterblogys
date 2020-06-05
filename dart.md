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
Les boucles sont utilisées pour parcourir les element d'un table,d'une collection ou dictionnaire dans certains langage ou des objects dans d'autres. Voila comment on les utilisent:
La boucle for :
{% highlight dart %}
void main() {
  print('MindDev - Dart for Loop');
  for (int i = 1; i <= 5; i++) {
    print(i);
  }
}
{% endhighlight %}
**List**
une List est un table  et on peut recuperer un element de la sort
{% highlight dart %}
List a = [1,2,3] #Une list homogene;
print(a[0]);
{% endhighlight %}
L'index de la liste commence de 0 à n-1
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
exemple d'une List heterogene:
{% highlight dart %}
  dynamic a = [1,"adam",2.5] #Une list heterogene;
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

pour acceder a la valeur de i on procede de la maniere suivant ${i} ou $i,le deux syntaxe sont valides.

forEach
{% highlight dart %}
void main() {
  var list = ['apples', 'bananas', 'oranges'];
  list.forEach((item) {
    print('${list.indexOf(item)}: $item');
  });
}
{% endhighlight %}
forEach est un iterateur