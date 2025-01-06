# French

Comment l'utiliser:

* télécharger le repo
* extraire le fichier zip (il est léger, seulement 30 éléments contre 4000 dans l'original)
* envoyer sur drive en respectant l'architecture de dossiers précisée dans la 2e cellule du notebook
* run le notebook (dans un colaboratory par exemple)

Objectifs de ce notebook:

* (obj 1) tenter de recoder une version simple de TokenCompose à partir de ma connaissance des bibliothèques d'Hugging Face et de la lecture du papier https://github.com/mlpc-ucsd/TokenCompose
* (obj 1.1) cela doit nous forcer à aller à l'essentiel et comprendre en profondeur le fonctionnement de la méthode TokenCompose, du réseau Stable Diffusion, des outils fournis par Hugging Face
* (obj 1.2) cela permet aussi de comprendre les difficultés que les chercheurs ont pu rencontrer
* (obj 1.3) dans l'idéal, cela doit aussi permettre de comparer les résultats avec le modèle Stable Diffusion (en retirant facilement les losses token et pixel) et comparer aussi avec les résultats de TokenCompose, pour voir si une petite différence dans l'interprétation de leur méthode implique de grands changements de résultats ou pas

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

How to use it:

* download the repo
* extract the zip file (it's light, only 30 items compared with 4000 in the original)
* send to drive, respecting the folder architecture specified in the 2nd cell of the notebook
* run the notebook (in a colaboratory for example)

Objectives of this notebook:

* (obj 1) try to recode a simple version of TokenCompose based on my knowledge of the Hugging Face libraries and my reading of the https://github.com/mlpc-ucsd/TokenCompose paper.
* (obj 1.1) this should force us to get to the heart of the matter and understand in depth how the TokenCompose method, the Stable Diffusion network and the tools provided by Hugging Face work.
* (obj 1.2) it should also help us understand the difficulties that the researchers may have encountered
* (obj 1.3) ideally, this should also enable the results to be compared with the Stable Diffusion model (by easily removing the token and pixel losses) and also compared with the TokenCompose results, to see whether a small difference in the interpretation of their method implies major changes in the results or not.

What I have done so far:
* study in detail the code on Hugging Face of S.D.1.4 (obj 1.1 well advanced)
* read the paper (-> there's an error in the schema but overall a good paper)
* try to run TokenCompose (-> I had a library problem)
* recode my own TokenCompose using my knowledge of the paper and Hugging Face modules. I figured this would ultimately be the best way to understand what was going on in TokenCompose and unet. I didn't quite understand how to get the activation map (in the attentions layers) because dimension [1,4096,320] (I understood that 4096 is for 64x64 because the latent space is 64x64 but I didn't understand the relationship between 320 and the dimensions of the text embedding.

What I learned about TokenCompose:
* well-written paper except for a small error on figure 3 (the arrows are not connected correctly).
* I've realised that the real difficulty they've had to face is recovering the attentions (because I haven't succeeded so far)... but I've understood that theoretically with a `hook` it should be possible (obj 1.2 well advanced)

General lessons:
* I learned how to manipulate Hugging Face (the platform).
* I realised that Hugging Face is designed for models to be used, but not necessarily fine-tuned. For example, SD14 has no forward function, only a __call__ function.
* You can easily access the template code on Hugging Face, but it's difficult to read because there are so many classes nested inside each other.


