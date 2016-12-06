#Programmation Objet en Java

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
    
