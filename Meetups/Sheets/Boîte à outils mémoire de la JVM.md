#Partie I :

###Anti pattern leaks memory :
Collections statiques
Mauvaise implémentation equals/hashcode
ThreadLocal : associer un état à un thread
Resources non fermées 

###Types de GC :
1-Classiques : parallel/ throughput : les objets ont une vie courtes Young et Old
2- Serial : utilise un seul thread
3- CMS : concurrent avec l'applicatif
4- G1 Depuis Jdk7 : éviter de faire des GC Monica Beckwith


##Jvm : 
heap + stacks de thread + permGen (pool de strings déplacé vers la heap depuis la jdk7) + metaspace (depuis jdk8)

Allocation en dehors de la heap (off-heap) pour des objets genre cache : allocateDirect 

Code cache : stocker le code exécuté pour la performance de la jvm

#Partie II : diagnostic :

constat : outofmemory + lenteur
Calcul de moyenne mobile : moyenner sur plusieurs montants de trades

##Comment s'y prendre?
Mesurer la performance : temps de GC, nombre, GC le plus long, ...
Investigation : pour trouver les causes
Changement
Re mesurer la performance etc

Paramétrer la JVM pour mesurer les performances :
- xms et xmx
- ‎activer les logs de GC printGCDetails et gc.log
( pas sous JRE9 -XLog)

- mesurer par jVisualVM ( pas sur jdk9) jConsole, ...
- ‎gc.log : GC Allocationfailure : GC minor
Un outil pour voir les logs GC et les analyser

Outil : GCViewer (github) /Censum(payant)/ GCeasy(optimisations, déposer son fichier de log)

Throughput : l'application en dehors du GC
Visualiser en graphique

Que faire si on active pas les logs en prod (en jdk9 on peut me faire à chaud jcmd ...)
jps : lister les process java 

Jstat avec le pid heap et GC

D'où viennent ces objets dans notre old generation

##Why ?

Quels sont nos objets présents dans la heap?
Histogramme des objets dans la heap : 
Jmap -histo
Jcmd
Jhsdb : débugger de jvm
Jmap
Jcmd
Jhsdb

Au lieu de parcourir le code : obtenir un heap dump : +HeapDumpOnOutOfMemory
Analyser un heap dump
Memory analyzer tool
Dominator tree
Leak suspects

JOverflow( stop wasting your heap)
YourKit
JVisualVM
JProfiler

Tous les trades en mémoire 

Comment diminuer le GC minor?