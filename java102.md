#Programmation Objet en Java


##Introduction

La programmation informatique est une discipline relativement jeune , en perpétuelle évolution et caractérisée par des révolutions successives dans les outils et techniques permettant de produire le code.
On peut également noter que chaque langage de programmation est client d'une couche inférieure et ce jusqu'a l'assembleur client du jeu d'instruction du processeur.

Comme nous l'avons vu en cours , le fonctionnement de l'ordinateur , au niveau assembleur / Langage machine , n'offre l'accès qu'a des capacités limitées au regard de la structure du programme . Les premières capacités d'abstraction (procédure , syntaxe de boucle simplifiée , pointeurs ...) sont apparues avec les premiers langage de haut niveau (PASCAL ,COBOL) et ont été formalisée par le langage C.

Le paradigme de programmation procédurale permet la décomposition fonctionnelle d'une application , ce qui autorise une forme de structure basique dans le programme, simplifiant la réutilisation de code , la déclaration et l'exploitation des structures de données statiques (tableaux).
Ce simple gain à grandement supporté la démocratisation de l'informatique en permettant à un public de programmeurs beaucoup plus large de créer des programmes sans maitriser au préalable l'ensemble des concepts sous-jacents (fonctionnement processeur / mémoire etc ..)

Cependant , la décomposition fonctionnelle rencontre également ses limites car bien qu'elle permette la réutilisation du code , elle ne permet pas la spécialisation du code , un concept dont l'importance grandit paralèllement à la taille d'un programme .

De plus elle aboutit en bout de compte à une forme d'ogranisation trop friable pour supporter les nombreuses **itérations** et **changement de design** caractérisant le développement des logiciels modernes.

L'intégration de la couche objet pour C (C++) , permet de conquérir les problèmes de structure du programme , grâce à l'application des concepts objets et des Design Pattern . Ce langage , aujourd'hui utilisé pour la programmation d'OS (Linux,Windows) offre le meilleur rapport Structure / Performance. 
Cependant il s'agit d'un langage procédural auquel une couche objet à été ajouté  , et la programmation d'un projet d'ampleur est une tâche lourde , nécessitant une précision technique importante . De plus la portabilité du code C++ est extrêmement limitée puisqu'il doit être refactoré et recompilé pour chaque plateforme (Win/Linux/Mac/Android/iOS etc...).


**Java** et **C#** proposent une approche fondamentalement différente de la programmation . Ces langages s'exécutent sur une machine virtuelle (JVM pour Java / CLR pour C#) dont le support multi-plateformes est assuré par l'éditeur . La gestion de la mémoire est prise en charge par le langage et tous les deux sont des langages entièrement objet (Tous les types de base accessibles sont des objets).

Ces langages mettent à dispotion même d'un programmeur seul , la puissance de 50 années de recherche/expérience en terme de conception de code informatique et sont généralement ceux utilisés par les API spécialisées modernes , comme c'est le cas pour Android.

##Les Bases

La couche objet en Java est implémentée avec les éléments suivants (du moins abstrait au plus abstrait)
   
###Les Eléments actifs au Runtime   
   
 * La classe statique
    * Une classe statique n'a pas besoin d'être instanciée , elle existe dès l'initialisation du programme , et ses attributs publics (Méthodes / Propriétés) sont accessible à l'ensemble du programme
    * A ce titre le code contenu dans une classe statique peut être vu comme une extension de Java , spécifique à notre programme , car tout comme l'ensemble des fonctions du langage , il peut être appellé de tout point dans le programme.
    * Pour cette raison , le contenu des classes statiques doit être considéré avec soin , elle hébergent généralement l'interfacage avec les sources de données externes au programme (système de fichier / base de données / Accès HTTP etc ...).
    * Le but ultime d'une classe statique est de fournir des fonctions transversales dans notre programme (Interfacage externe / Pattern créationnels ...) dans le but de simplifier l'écriture , l'expressivité , la concision et la lisibilité du code client 
    
  * L'objet (classe non statique instanciée)
    * Un objet n'a d'existence au runtime que si il est instancié.
    * L'instanciation d'un objet s'effectue par le biais d'une fonction spéciale , le constructeur
    * Un objet est une représentation au runtime d'un type défini (Classe)
    * L'objet est l'unité conceptuelle et structurelle de base dans un langage de programmation moderne
    * Il peut être assimilé à un mini-programme dans le programme avec :
    
               | Programme | Objet
    -----------|-----------|-----------
    **Cycle de vie** | Lancement du programme | Instanciation
    | Exécution et exploitation | Opération au runtime
    | Fermeture du programme par l'utilisateur | destruction    
    **Champs / Méthodes privées** | Invisibles pour l'utilisateur |Invisibles pour le code client de l'objet
    **Propriétés / Méthodes publiques** | Fonctions haut niveau du programme | Méthodes publiques de l'objet
     | Configuration et Interface Utilisateur | Constructeur et Propriétés publiques
    
    
#####    L'objet est l'unité fonctionnelle de base au Runtime , **encapsulant**  code et de données . La structure d'un programme quelque soit sa taille et sa complexité peut être rationalisée par l'application de Design Patterns qui définissent leurs modalités de création (Créationnel), d'agencement (Structurel) et d'interopérabilité (Comportemental) pendant l'exécution.
    
###Les Eléments de Design
 * La classe
    * La classe est l'élément de base du design objet , elle permet de définir une maquette de programme auto-contenu qui deviendra un objet au runtime , les mécanismes d'héritage permettent de **spécialiser une classe** (mot-clé extends)
    * Une classe peut également être **spécifiée** par une interface (mot clé implements)
 * La classe abstraite
    * La classe abstraite est une étape intermédiaire entre la classe (exposant des méthodes concrètes)et l'interface(spécifiant des méthodes abstraite) , tout comme l'interface , elle ne peut être instanciée directement , mais elle peut contenir des méthodes concrètes
 * L'interface
    * L'interface permet de spécifier un ensemble de fonction que doit implementer toute classe souscrivant à cette interface . Ce mécanisme permet notamment le polymorphisme niveau objet , largement utilisé par les Design Patterns
    
