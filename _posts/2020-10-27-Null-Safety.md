---
layout: post
title:  "Pourquoi Null Safety ?"
date:   2020-10-27 23:20:03 +0100
author: AdamMusa
url: /null-safety/dart
---

![alt text](/assets/images/dart.png){: width=50;height:60; style="float:left; padding:16px;border-radius:50%;height:100px;"}
<br> AdamMusa [Follow](https://twitter.com/AdamMusaAly/)<br>
2,Juin 2020 16min


Dart est un langage de type sécurisé. Cela signifie que lorsque vous obtenez une variable d'un certain type, le compilateur peut garantir qu'elle est de ce type. Mais la sécurité de type en soi ne garantit pas que la variable ne l'est pas null.
Les erreurs nulles sont très courantes. Une recherche sur GitHub conduit à des milliers de problèmes causés par des valeurs nulles dans le code Dart, et encore plus de milliers de commits essayant de résoudre ces problèmes.
Essayez de voir si vous pouvez repérer les problèmes de nullabilité dans l'exemple de code suivant:

{% highlight dart %}
  void printLengths(List<File> files) {
  for (var file in files) {
    print(file.lengthSync());
  }
}
{% endhighlight %}

Cette fonction échouera certainement si elle est appelée avec null, mais il y a un deuxième cas à considérer:

{% highlight dart %}
 void main() {
  // Error case 1: passing a null to files.
  printLengths(null);
  // Error case 2: passing list of files, containing a null item.
  printLengths([File('filename1'), File('filename2'), null]);
}
{% endhighlight %}

**Sound null safety**

Sound null safety de Dart est saine . Cela signifie que Dart est sûr à 100% que la filesliste et les éléments qu'elle contient ne peuvent pas être null dans l'exemple ci-dessus. Lorsque Dart analyse votre code et détermine qu'une variable est non-nullable, cette variable est toujours non-nullable: si vous inspectez votre code en cours d'exécution dans le débogueur, vous verrez que la non-nullability est conservée au moment de l'exécution. En revanche, certaines autres implémentations sont défectueuses et, dans de nombreux cas, doivent encore effectuer des vérifications nulles à l'exécution. Dart partage Null Safety avec Swift, mais pas beaucoup d'autres langages de programmation.
La solidité de Sound null safety de Dart a une autre implication bienvenue: cela signifie que vos programmes peuvent être plus petits et plus rapides. Parce que Dart est vraiment sûr que ce files n'est jamais le cas null, Dart peut optimiser. Par exemple, le compilateur Dart ahead-of-time (AOT) peut produire du code natif plus petit et plus rapide, car il n'a pas besoin d'ajouter des vérifications pour les valeurs nulles lorsqu'il sait qu'une variable ne l'est pas null.
Nous avons vu des résultats préliminaires très prometteurs. Par exemple, **l'équipe de Google chargé du projet dart** a constaté une amélioration des performances de 19% dans un microbenchmark qui émule les modèles de rendu typiques du framework Flutter.

Avec Null Safety, vous pouvez raisonner votre code avec plus de confiance. Fini les erreurs de déréférencement nul lors de l'exécution. Au lieu de cela, vous obtenez des erreurs statiques lorsque vous codez.
Avec  Null Safety, l'analyseur Dart applique les bonnes pratiques. Par exemple, il s'assure que vous vérifiez la valeur NULL avant de lire une variable Nullable. Et parce que la  Null Safety de Dart est saine, les compilateurs et les environnements d'exécution Dart peuvent optimiser les vérifications internes de null, de sorte que les applications peuvent être plus rapides et plus petites.

Les nouveaux opérateurs et mots - clés liés à la sécurité comprennent nulle ?, !et late. Si vous avez utilisé Kotlin, TypeScript ou C#, la syntaxe de la  Null Safety peut vous sembler familière. C'est par conception: le langage Dart se veut sans surprise.
Vous pouvez essayer la Null Safety dans votre environnement de développement normal en configurant votre projet pour utiliser un SDK d'aperçu technique.

**Déclaration de variables avec Null Safety**

Si la variable peut avoir la valeur null, ajoutez? à sa déclaration de type:

{% highlight dart %}
    int? aNullableInt = null;
{% endhighlight %}

Si vous savez qu'une variable non nullable sera initialisée à une valeur non nulle avant d'être utilisée, mais que l'analyseur Dart n'est pas d'accord, insérez late avant le type de la variable:

{% highlight dart %}
class IntProvider {
  late int aRealInt;
  
  IntProvider() {
    aRealInt = calculate();
  }
}
{% endhighlight %}

**Le late mot-clé a deux effets:**

L'analyseur ne vous oblige pas à initialiser immédiatement une late variable à une valeur non nulle.
Le runtime initialise paresseusement la late variable. Par exemple, si une variable d'instance non Nullable doit être calculée, l'ajout du late modificateur retarde le calcul jusqu'à la première utilisation de la variable d'instance.

**Utiliser des variables et des expressions**

Avec la Null Safety, l'analyseur Dart génère des erreurs lorsqu'il trouve une valeur Nullable où une valeur non NULL est requise. Ce n'est pas aussi grave que cela en a l'air: l'analyseur peut souvent reconnaître lorsqu'une variable ou une expression à l'intérieur d'une fonction a un type Nullable mais ne peut pas avoir une valeur Null.

Lorsque vous utilisez une variable ou une expression Nullable, veillez à gérer les valeurs Null. Par exemple, vous pouvez utiliser une if instruction, l' ??opérateur ou l' ?.opérateur pour gérer d'éventuelles valeurs nulles.

Voici un exemple d'utilisation de l' ??opérateur pour éviter de définir une variable non nullable sur null:

{% highlight dart %}
int value = aNullableInt ?? 0; // 0 if it's null; otherwise, the integer
{% endhighlight %}

**Voici un code similaire, mais avec une if instruction qui vérifie la valeur null:**

{% highlight dart %}
int definitelyInt(int? aNullableInt) {
  if (aNullableInt == null) {
    return 0;
  }
  return aNullableInt; // Can't be null!
}
{% endhighlight %}

Si vous êtes sûr qu'une expression avec un type Nullable n'est pas NULL, vous pouvez ajouter !pour que Dart la traite comme non Nullable:

{% highlight dart %}
int? aNullableInt = 2;
int value = aNullableInt!; // `aNullableInt!` is an int.
// This throws if aNullableInt is null.
{% endhighlight %}

Si vous avez besoin de changer le type d'une variable Nullable - au-delà de ce que l' !opérateur peut faire - vous pouvez utiliser l' opérateur de transtypage (as) . L'exemple suivant utilise aspour convertir un num?en un int:

{% highlight dart %}
return maybeNum() as int;
{% endhighlight %}

Une fois que vous avez opté pour la sécurité null, vous ne pouvez pas utiliser l' opérateur d'accès. aux membres ( ) si l'opérande peut être nul. Au lieu de cela, vous pouvez utiliser la version compatible NULL de cet opérateur ( ?.):

{% highlight dart %}
double? d;  
print(d?.floor()); // Uses `?.` instead of `.` to invoke `floor()`.
{% endhighlight %}

**Rendre Null Safety plus facile à utiliser**


Notez à quel point Dart est assez intelligent pour réaliser qu'au moment où nous transmettons cette if instruction, la loudnessvariable ne peut pas l' être null. Et donc Dart nous permet d'appeler la clamp()méthode sans sauter à travers les cerceaux. Cette commodité est rendue possible par quelque chose appelé analyse de flux : l'analyseur Dart parcourt votre code comme s'il l'exécutait, trouvant automatiquement des informations supplémentaires sur votre code.
Voici un autre exemple, qui montre un cas où Dart peut être sûr qu'une variable est non nulle car nous lui affectons toujours une valeur non nulle:

{% highlight dart %}
int sign(int x) {
  // The result is non-nullable.
  int result;
  if (x >= 0) {
    result = 1;
  } else {
    result = -1;
  }
  // By this point, Dart knows the result cannot be null.
  return result;
}
{% endhighlight %}

Si vous supprimez l'une des affectations ci-dessus (par exemple, en supprimant la result = -1;ligne), Dart ne peut pas garantir que ce resultsera non nul: vous obtiendrez une erreur statique et votre code ne sera pas compilé.
L'analyse de flux ne fonctionne qu'à l'intérieur des fonctions. Si vous avez une variable globale ou un champ de classe, Dart ne peut pas garantir à quel moment la valeur lui sera attribuée. Dart ne peut pas modéliser le flux de l'ensemble de votre application. Pour cette raison, vous pouvez utiliser le nouveau late mot-clé lorsque vous savez qu'une variable sera non nulle avant de la lire pour la première fois, mais que vous ne pouvez pas l'initialiser immédiatement.

{% highlight dart %}
class Goo {
  late Viscosity v;
  Goo(Material m) {
    v = m.computeViscosity();
  }
}
{% endhighlight %}

Notez que ce v n'est pas nul, bien qu'il démarre non initialisé. Dart vous fait confiance que vous n'essaierez pas de lire v avant de lui attribuer une valeur non nulle et que votre code se compile sans erreur.

**Conclusion :**

**Bravooo!!!** vous êtes déjà à l'aise avec Null Safety.

 **Sound null safety** est une caractéristique distinctive de Dart qui vous aide à écrire du code moins sujet aux erreurs et à obtenir de meilleures performances. J'espérons que vous allez expérimenter la fonctionnalité . Meric pour votre temps