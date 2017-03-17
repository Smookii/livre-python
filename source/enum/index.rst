ENUM
====

.. image:: ../_static/python_logo.png
   :align: right
   :alt: Python logo

Par Axel Bento da Silva 

1.Introduction
------------


1.1.Définition

L'enumération est un liste de noms symboliques lié à des valeurs constantes, on peu donc avec l'enumération remplacé des valeurs entière pas très parlante par des nom plus logique.

Le principale attrait de l'enumération est donc d'écrire du code plus lisible et humain.

En python le 'enum.py' est un module qui contient 4 classes d'enumération différentes : Enum, IntEnum, Flag, intFlag, il contient quelques fonctionnalités supplémentaires.

2.Utilisation
-------------

Il faut faire attention à ce pourquoi on l'utilise, une enumération n'est nécessaire que pour représenté un objet très simple ou l'état d'un objet complexe.


2.1.Un mauvais exemple

Un mauvais exmple d'utilisation est par exemple celui de créer un enum pour les animaux :

.. code-block:: mauvaisExemple_01

	>>> class Annimal(Enum):
			Dog = 0
			Cat = 1
			Bird = 2



Un annimal est un objet bien trop complexe qui se définit par plein d'attribut (son nom, son poids, sa taille, etc...), il est donc bien plus censé de créer une classe Annimal à part, 
qui pourra d'ailleurs implémenter des méthodes telle que manger(), dormir(), etc... et dans ce cas on pourrais envisager d'ajouter un attribut  
enumérer pour définir l'éspèces.

2.2.Un bon exemple

Un bon exemple d'utilisation est celui du feu vert, on peu représenté l'état d'un feu rouge par une simple variable entière qui varie de 0 à 2, mais cela nécéssite qu'on garde
en tête quel chiffre correpond à quoi, etc...
Il suffit donc de remplacé cette variable entirère par une enumération de ce type :

.. code-block:: bonExemple_01

	>>> class StateLight(Enum):
			RED = 0
			ORANGE = 1
			GREEN = 2

Dans cette exemple ci-dessus, bien que les états soit plus parlant, le fait d'utiliser des valeurs numériques peu poser des problèmes dans la suite du programme, par exemple si 
le feu est actuellement à l'état ORANGE, et que nous voulons afficher la valeur de ce feu c'est la valeur 1 qui apparaîtra :

.. code-block:: bonExemple_02

	>>>light = StateLight['ORANGE']
	>>>light.name
	'ORANGE'
	>>>light.value
	1

Pour contrer ce problèmes il suffit de remplacé les valeurs numériques par des string plus parlant :

.. code-block:: bonExemple_03
	
	>>> class StateLight(Enum)
			RED = "Rouge"
			ORANGE = "Orange"
			GREEN = "Vert"
		
	>>>light = StateLight['RED']
	>>>light.name
	'RED'
	>>>light.value
	'rouge'
	
2.3.Exemple concret 

Comme exemple concret nous avons de nombreux librairies de différents language qui propose une enumération de couleurs de base.
Donc plustôt que de devoir connaître tous les codes couleurs, le programmeur peu utilier le nom des couleurs :

EnumColor_
	
3. Attribut du module
---------------------

3.1. Enum

Enum, est la classe de base pour la création d'enumération. On peu définir ces enumérations de différentes façon.

.. code-block:: Enum_01

	>>> class StateLight(Enum):
			RED = 1
			ORANGE = 2
			GREEN = 3

est égal à :

.. code-block:: Enum_02

	>>> StateLight = Enum('Light', 'RED ORANGE GREEN')
	>>> List(StageLight)
	[<Light.RED: 1>, <Light.ORANGE: 2>, <Light.GREEN: 3>,]

ou 

.. code-block:: Enum_03

	>>> StateLight = Enum('RED=1,ORANGE=2, GREEN=3')

ou encore comme vue dans l'exemple 2.2. on peu remplacé les valeurs numériques par des valeurs plus parlante.

.. code-block:: Enum_04

	>>> StateLight = Enum('RED='Rouge',ORANGE='Orange', GREEN='Vert')
	>>> StageLight.GREEN
	Vert

3.2. IntEnum

3.3. IntFlag

3.4. Flag


4.Conclusion
------------



5.Bibliographie
---------------
.. _EnumColor: http://matplotlib.org/examples/color/named_colors.html
	


