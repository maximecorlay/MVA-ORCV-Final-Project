# French

Comment l'utiliser:

* télécharger le repo
* extraire le fichier zip (il est léger, seulement 30 éléments contre 4000 dans l'original)
* envoyer sur drive en respectant l'architecture de dossiers précisée dans la 2e cellule du notebook
* run le notebook (dans un colaboratory par exemple)

Objectifs de ce notebook:

* (obj 1) tenter de recoder une version simple de TokenCompose à partir de ma connaissance des bibliothèques d'Hugging Face et de la lecture du papier https://github.com/mlpc-ucsd/TokenCompose
** (obj 1.1) cela doit nous forcer à aller à l'essentiel et comprendre en profondeur le fonctionnement de la méthode TokenCompose, du réseau Stable Diffusion, des outils fournis par Hugging Face
** (obj 1.2) cela permet aussi de comprendre les difficultés que les chercheurs ont pu rencontrer
** (obj 1.3) dans l'idéal, cela doit aussi permettre de comparer les résultats avec le modèle Stable Diffusion (en retirant facilement les losses token et pixel) et comparer aussi avec les résultats de TokenCompose, pour voir si une petite différence dans l'interprétation de leur méthode implique de grands changements de résultats ou pas

Ce que j'ai fait jusque là :
* étudier en détail le code sur Hugging Face de S.D.1.4 (obj 1.1 bien avancé)
* lire le papier (-> il y a une erreur sur le schéma mais globalement bon papier)
* tenter d'exécuter TokenCompose (-> j'ai eu un problème de bibliothèque)
* recoder mon propre TokenCompose grâce à ma connaissance du papier et des modules d'Hugging Face. Je me suis dit que ce serait finalement le meilleur moyen de comprendre ce qui se passe dans TokenCompose et unet. Je n'ai pas bien compris comment récupérer la carte des activations (dans les attentions layers) car dimension [1,4096,320] (j'ai bien compris que 4096 c'est pour 64x64 car l'espace latent est 64x64 mais je n'ai pas compris le rapport entre 320 et les dimensions de l'embedding textuel.

Mes enseignements sur TokenCompose:
* papier bien rédigé sauf petite erreur sur la figure 3 (les flèches sont mal reliées)
* j'ai pris conscience que la vraie difficulté à laquelle ils ont dû faire face est de récupérer les attentions (car je n'ai pas réussi pour l'instant)... mais j'ai bien compris que théoriquement avec un `hook` ça doit être possible (obj 1.2 bien avancé)

Enseignements généraux:
* j'ai appris à manipuler Hugging Face (la plateforme)
* J'ai réalisé qu'Hugging Face est faite pour que les modèles soient utilisés, mais pas forcément fine tunés. Par exemple, SD14 n'a pas de fonction forward. il n'a qu'une fonction __call__
* on peut facilement accéder au code des modèles sur Hugging Face mais difficile à lire car beaucoup de classes imbriquées les unes dans les autres

# English

