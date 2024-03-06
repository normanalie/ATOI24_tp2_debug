# TP2 - ALIE Norman

## Exercice 1
1. Le code génère une image avec des coulers et des formùes en utilisant le laplacien et des maths
2. En traitement du signal, la convolution est utilisée pour appliquer appliquer un filtre filtre(t) à un signal en combinant la fonction signal(t) et la fonction filtre(t)
Le laplacien est utilisé pour detecter des changements brusques, souvent des bords sur une image
3. Le code 'nest pas fonctionnel -> il génère une erreur de segmentation
4. Le bug était une tentative d'accès à l'index [-1] du tableau ce qui créé une erreur de segmentation -> Première aparition main.c:23 identifié grace à `lldb`
5. Pour le corriger on part de l'indice 1 dans la boucle ce qui fait un 1-1=0 qui est un index valide.