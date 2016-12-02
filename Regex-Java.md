#Expressions régulières en Java

Le support des expressions régulières est fourni par le package java.util.regex.\* , qui doit être importé comme suit

```java
import java.util.regex.*;
```

##Echappement de caractères

En java , le backslash '\' sert d'origine à identifier certains caractères spéciaux dans les chaînes de caractère (String) , exemple \n permet d'indiquer un retour à la ligne ou \t une tabulation .

Pour cette raison les String "Hardcodée" (inscrites par syntaxe littérale) servant aux expressions réguilères doivents être doublement échappées . _ex : "il y a \d chien" doit être modifiée en "il y a \\d chiens"_.

La stratégie utilisée pour contourner ce problème pour le code de production est de stocker les regex sous forme de Properties ou un fichier de resource , ou elle ne sont pas soumise à la règle du double échappement

##Match d'un String

Travailler avec les Regex sous Java requiert généralement l'instanciation d'un objet **Pattern** et d'un objet **Matcher** , cependant si l'on cherche uniquement à tester si le Regex valide un string ou non , la méthode statique Pattern.matches() peut être utilisée

```java
boolean isMatch = Pattern.matches(String regex, String inputStr)
```

A contrario , si l'on souhaite également récupérer les valeurs matchées par le Regex , on préférera le compiler pour instancier un nouveau Pattern et utiliser une instance de Matcher pour travailler sur les résultats .

```java
Pattern ptrn = Pattern.compile(String regex)
Matcher matcher = ptrn.matcher(String inputStr)
```

```java
// Utilisons une expression régulière pour capturer les éléments d'une date.
Pattern ptrn = Pattern.compile("([a-zA-Z]+) (\\d+)");
Matcher matcher = ptrn.matcher("June 24");
if (matcher.matches()) {

    // Les indices (positions des caractères Matchés) peuvent être lus via .start() et .end() 
    // sur l'objet Matcher
    // Cela va afficher [0, 7], car tout le String est matché
    
    System.out.println("Match at index [" + matcher.start() + 
        ", " + matcher.end() + ")");

    // Pour obtenir le texte matché , lire .group() sur l'objet Matcher
    // cela va afficher "June 24"
    System.out.println("Match: " + matcher.group());
}
```

##Groupes de capture

On peut également itérer sur les groupes de capture extraits par le Matcher

```java

String pattern = "([a-zA-Z]+) (\\d+)";
Pattern ptrn = Pattern.compile("([a-zA-Z]+) (\\d+)");
Matcher matcher = ptrn.matcher("June 24, August 9, Dec 12");

// Ceci va afficher chacun des Match et leur index dans le String Matché
//
//   June 24 at index [0, 7)
//   August 9 at index [9, 17)
//   Dec 12 at index [19, 25)

while (matcher.find()) {
    System.out.println(String.format("Match: %s at index [%d, %d]",
        matcher.group(), matcher.start(), matcher.end()));
}

// Si nous devons réeffectuer la traverse , utiliser .reset() sur l'objet Matcher 
// matcher pour replacer l'iterateur en début de chaine
matcher.reset();


while (matcher.find()) {
    // Affiche le nombre de groupes capturés dans ce Match
    System.out.println(String.format("%d groups captured", 
        matcher.groupCount()));

    // Affiche le mois et le jour .  Attention le premier groupe est toujours 
    // l'ensemble du texte matché , donc on récupère le mois à l'index 1
    
    System.out.println("Month: " + matcher.group(1) + ", Day: " + 
        matcher.group(2));

    // Chaque group à également ses indices de départ et de fin , relatif à la 
    // chaine en entrée
    System.out.println(String.format("Month found at[%d, %d)", 
        matcher.start(1), matcher.end(1)));
}
```
##Trouver et remplacer dans les Strings

Une autre tâche commun&ément effectuée est de trouver et remplacer une partie d'un string via les regex , par exemple , pour remplacer toutes les instances d'un vieux domaine mail , ou changer l'ordre dans un texte .
En Java les méthodes .replaceAll() et .replaceFirst() de l'objet Matcher permettent ce type de traitement . Chacune de ces méthodes commencent par reset le matcher en début de string et l'arrête soit en fin de String , soit en fin de première occurence de match

La String de remplacement peut contenir des références aux groupes capturés dans le pattern (en utilisant le signe **$**), ou une String littérale

```java
String replacedString = matcher.replaceAll(String inputStr)
String replacedString = matcher.replaceFirst(String inputStr)
```
```java
// On veut renverser l'ordre date/mois dans nos strings.
// Notez que la String de remplacement contient également des métacaractère 
// (les "back references" aux groupes de capture) 

Pattern ptrn = Pattern.compile("([a-zA-Z]+) (\\d+)");
Matcher matcher = ptrn.matcher("June 24, August 9, Dec 12");

// Ceci va renverser l'ordre et imprimer
//   24 of June, 9 of August, 12 of Dec
//
// Remember that the first group is always the full matched text, so the 
// month and day indices start from 1 instead of zero.
String replacedString = matcher.replaceAll("$2 of $1");
System.out.println(replacedString);
```

##Flag pour Pattern

Quelques flags sont disponible lors de la phase de compilation du pattern , offrant des
modification sur le comportement du moteur d'expressions régulières

* **Pattern.CASE_INSENSITIVE** _Pas de contrôle de la capitalisation ex: A = a_
* **Pattern.MULTILINE** _Nécessaire si la String en entrée contient des retour à la ligne et que votre Regex doit permettre de matcher les lignes \n individuellement avec **^** et **$** plutot que l'ensemble du String_
* **Pattern.DOTALL** _Permet au point . de matcher les nouvelles lignes \n également_
* **Pattern.LITERAL** _Supprime la compilation des métacaractère et compile le Regex litérallement ex: \d va matcher \d plutot qu'un chiffre_


