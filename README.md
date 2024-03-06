# TP2 - ALIE Norman

## Exercice 1
1. Le code génère une image avec des coulers et des formùes en utilisant le laplacien et des maths
2. En traitement du signal, la convolution est utilisée pour appliquer appliquer un filtre filtre(t) à un signal en combinant la fonction signal(t) et la fonction filtre(t)
Le laplacien est utilisé pour detecter des changements brusques, souvent des bords sur une image
3. Le code 'nest pas fonctionnel -> il génère une erreur de segmentation
4. Le bug était une tentative d'accès à l'index [-1] du tableau ce qui créé une erreur de segmentation -> Première aparition main.c:23 identifié grace à `lldb`
5. Pour le corriger on part de l'indice 1 dans la boucle ce qui fait un 1-1=0 qui est un index valide.

## Exercice 2
1. 
   - Fonction 1: i va jusqu'à size or c'est un tableau donc elle ne devrai pas atteindre size
   - Fonction 2: i va jusqu'a size+50 -> en dehors du tableau
   - Fonction 3: i va jusqu'a size*1000
2.
    - Fonction 1: pas de segfault mais un comportement faux qui va écrire à une mauvaise adresses dans le heap
    - Fonction 2: pas de segfault mais un comportement faux qui va écrire à une mauvaise adresses dans le heap
    - Fonction 3: Segfault
3. `lldb` avec `llef` intègre ASAN et permet d'identifier les erreurs de segmentations qu'elles soient sur la même page ou non. Dans les trois cas `lldb` donne une erreur de segmentation: _Heap buffer overflow_ en précisant la ligne à laquelle s'est produite l'interruption de l'execution. 
4.  Non une corruption ne mêne pas toujours au plantage. Une corruption en dehors du zone mémoire du process mêne à un plantage inité par l'OS. Une corruption dans un zone mémoire du process est à gérer en interne par le process. 


## Exercice 3
1. Une fuite de mémoire est une allocation dynamique qui n'est jamais libérée ce qui entraine une utilisation excessive de la mémoire.
2. La fuite est identifiable avec Valgrind -> On essaie de free des pointeurs NULL et on ne free pas les vraies addresses allouées précédement.
3. On retire la ligne `segments[i++] = NULL;`

## Exercice 4
1. Le programme fait la somme des elements dans le tableau
2. Le programme donne un résultat peut etre faux car il additionne aussi la valeur de sum.
3. Avec gdb on place un breakpoint à la ligne 9 et on affiche la valeur de sum avec `v sum`

## Exercice 5
1. Le code est vulnérable car l'entrée de l'utilisateur n'est pas protégée, il a donc accès à toute la stack
2. La stack au moment de l'appel a vulnerable_function

|STACK|VALUE|
|-|-|
|password_is_good|0|
|buffer[7]|?|
|buffer[6]|?|
|buffer[5]|?|
|buffer[4]|?|
|buffer[3]|?|
|buffer[2]|?|
|buffer[1]|?|
|buffer[0]|?|

3. Pour déclencher l'erreur il faut entrer assez de caractère (9 ou +) pour écrire 98 aka `b`dans password_is_good
4. Pour casser le MDP, il faut entrer le caractère `b`dans password_is_good

