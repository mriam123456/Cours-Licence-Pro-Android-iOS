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
