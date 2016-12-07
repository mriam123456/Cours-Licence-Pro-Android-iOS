#Programmation Objet en Java


##Introduction

La programmation informatique est une discipline relativement jeune , en perpétuelle évolution et caractérisée par des révolutions successives dans les outils et technique permettant de produire le code.
On peut également noter que chaque langage de programmation est client d'une couche inférieure et ce jusqu'a l'assembleur client du jeu d'instruction du processeur.

Comme nous l'avons vu en cours , le fonctionnement de l'ordinateur , au niveau assembleur / Langage machine , n'offre l'accès qu'a des capacités limités compte tenu de la structure du programme . Les premières capacités d'abstraction (procédure , syntaxe de boucle simplifiée , pointeurs ...) sont apparues avec les premiers langage de haut niveau (PASCAL ,COBOL) et ont été formalisée par le langage C.

Le paradigme de programmation procédurale permet la décomposition fonctionnelle d'une application , ce qui autorise une forme de structure basique dans le programme, simplifiant la réutilisation de code , la déclaration et l'exploitation des structures de données statiques (tableaux).
Ce simple gain à grandement supporté la démocratisation de l'informatique en permettant à un public de programmeur beaucoup plus large de créer des programmes sans maitriser au préalable l'ensemble des concepts sous-jacents (fonctionnement processeur / mémoire etc ..)


Cependant , la décomposition fonctionnelle rencontre également ses limites car bien qu'elle permette la réutilisation du code , elle ne permet pas la spécialisation du code , un concept dont l'importance grandit paralèllement à la taille d'un programme . De plus elle aboutit en bout de compte à une forme d'ogranisation trop friable pour supporter les nombreuses itérations et changement de design caractérisant le développement des logiciels modernes.

##Les Bases

La couche objet en Java est implémentée avec les éléments suivants (du moins abstrait au plus abstrait)

 * L'objet (classe non statique instanciée)
    * Un objet n'a d'existence au runtime que si il est instancié
 * La classe statique
    * Une classe statique n'a pas besoin d'être instanciée , elle existe dès l'initialisation du programme
 * La classe
    * La classe est l'élément de base du design objet , elle permet de définir une maquette de programme auto-contenu , les mécanisme d'héritage permettent de **spécialiser une classe** (mot-clé extends)
    * Une classe peut également être **spécifiée** par une interface (mot clé implements)
 * La classe abstraite
    * La classe abstraite est une étape intermédiaire entre la classe (exposant des méthodes concrètes)et l'interface(spécifiant des méthodes abstraite) , tout comme l'interface , elle ne peut être instanciée directement , mais elle peut contenir des méthodes concrètes
 * L'interface
    * L'interface permet de spécifier un ensemble de fonction que doit implementer toute classe souscrivant à cette interface . Ce mécanisme permet notamment le polymorphisme niveau objet , largement utilisé par les Design Patterns
    
