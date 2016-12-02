#Expressions régulières en Java

Le support des expressions régulières est fourni par le package java.util.regex.\* , qui doit être importé comme suit

```java
import java.util.regex.*;
```

##Echappement de caractères

En java , le backslash '\' sert d'origine à identifier certains caractères spéciaux dans les chaînes de caractère (String) , exemple \n permet d'indiquer un retour à la ligne ou \t une tabulation .

Pour cette raison les String "Hardcodée" (inscrites par syntaxe littérale) servant aux expressions réguilères doivents être doublement échappées . _ex : "il y a \d chien" doit être modifiée en "il y a \\d chiens".

La stratégie utilisée pour contourner ce problème pour le code de production est de stocker les regex sous forme de Properties ou un fichier de resource , ou elle ne sont pas soumise à la règle du double échappement

##Match d'un String

Travailler avec les Regex sous Java requiert généralement l'instanciation d'un objet **Pattern** et d'un objet **Matcher** , cependant si l'on cherche uniquement à tester si le Regex valide un string ou non , la méthode statique Pattern.matches() peut être utilisée

```java
boolean isMatch = Pattern.matches(String regex, String inputStr)
```

