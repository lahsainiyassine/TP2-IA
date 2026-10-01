Dans ce deuxième TP, nous passons du texte nettoyé à sa transformation en données chiffrées compréhensibles par des algorithmes de Machine Learning. L'objectif est d'expérimenter et de comparer deux méthodes fondamentales de vectorisation textuelle avec la bibliothèque `scikit-learn` :
1. **Bag of Words (Sac de mots)** via `CountVectorizer`.
2. **TF-IDF (Term Frequency - Inverse Document Frequency)** via `TfidfVectorizer`.

---

## 🛠️ Ce qui a été réalisé

### 1. Modèle Bag of Words (BoW)
* Création d'un corpus de test composé de 3 phrases distinctes (thématiques sport et cinéma).
* Transformation du corpus en une matrice d'occurrences avec `CountVectorizer`.
* **Observations :**
  * Chaque colonne correspond à un mot unique du vocabulaire global.
  * Les valeurs représentent la fréquence brute du mot dans la phrase.
  * **Limites constatées :** Le modèle produit une matrice creuse (*sparse matrix*) remplie de zéros. De plus, il ignore complètement l'ordre des mots et la syntaxe, ce qui fait perdre le contexte (par exemple, une négation comme « pas bon » et « bon » partagent les mêmes mots mais ont un sens opposé).

### 2. Pondération TF-IDF
* Application de `TfidfVectorizer` sur le même corpus.
* Calcul du score pondéré pour chaque terme : multiplication de sa fréquence locale (TF) par sa rareté globale (IDF).
* **Observations :**
  * Les mots génériques ou répétés dans presque toutes les phrases voient leur score baisser automatiquement.
  * Les mots rares et distinctifs obtiennent un poids beaucoup plus important, ce qui permet de mieux séparer les phrases par sujet.

<img width="1152" height="790" alt="image" src="https://github.com/user-attachments/assets/cbac2c2f-cbe1-470b-b095-81800d5a9683" />
<img width="1245" height="702" alt="image" src="https://github.com/user-attachments/assets/c27e8fb7-70dd-446e-8f1d-a68567101fcb" />
