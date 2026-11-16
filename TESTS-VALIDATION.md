# 🧪 Guide de Tests et Validation - Séance 5

## 📋 Checklist de Validation Complète

### ✅ Test 1 : Vérification du Header
**Action :**
- Ouvrir http://localhost:5173/

**Résultat attendu :**
- ✓ Titre : "Mon Super Compteur React"
- ✓ Sous-titre : "Maitrise des Hooks fondamentaux useState et useEffect"
- ✓ Date du jour en français (ex: "samedi 8 novembre 2026")

---

### ✅ Test 2 : Compteur de Base
**Action :**
- Cliquer sur **+1** (3 fois)
- Cliquer sur **-1** (1 fois)
- Cliquer sur **Reset**

**Résultat attendu :**
- ✓ Après +1 (3x) : compteur affiche **3** en vert
- ✓ Après -1 (1x) : compteur affiche **2** en vert
- ✓ Après Reset : compteur affiche **0** en gris
- ✓ Aucun rechargement de page

---

### ✅ Test 3 : Pas d'Incrémentation Variable
**Action :**
1. Sélectionner pas **5** dans le menu déroulant
2. Cliquer sur **+5** (3 fois)

**Résultat attendu :**
- ✓ Compteur affiche **15** en vert
- ✓ Dernière action : "Ajout de 5"
- ✓ Total des clics : **3**
- ✓ Historique : "+5, +5, +5"

---

### ✅ Test 4 : Changement de Couleur
**Action :**
1. Reset le compteur
2. Cliquer sur **-1** (5 fois)

**Résultat attendu :**
- ✓ Compteur affiche **-5** en rouge
- ✓ La couleur du nombre est rouge (#ef4444)

---

### ✅ Test 5 : Persistance localStorage (Compteur)
**Action :**
1. Incrémenter le compteur à **25**
2. Ouvrir DevTools (F12) → Application → Local Storage
3. Rafraîchir la page (F5)

**Résultat attendu :**
- ✓ Clé `mon_compteur_valeur` avec valeur "25"
- ✓ Après F5, le compteur affiche toujours **25**
- ✓ Le titre de l'onglet affiche "Compteur : 25"

---

### ✅ Test 6 : Persistance de l'Historique (Défi 2)
**Action :**
1. Reset le compteur
2. Sélectionner pas **2**
3. Cliquer sur **+2** (4 fois)
4. Ouvrir DevTools (F12) → Application → Local Storage
5. Rafraîchir la page (F5)

**Résultat attendu :**
- ✓ Clé `mon_compteur_historique` contient : `["+2","+2","+2","+2"]`
- ✓ Après F5, l'historique affiche : "+2, +2, +2, +2"
- ✓ Le compteur affiche **8**
- ✓ Total des clics : **4**

---

### ✅ Test 7 : Limites +50 (Défi 1)
**Action :**
1. Reset le compteur
2. Sélectionner pas **10**
3. Cliquer sur **+10** jusqu'à atteindre **50**
4. Essayer de cliquer encore sur **+10**

**Résultat attendu :**
- ✓ À 50, le compteur s'arrête
- ✓ Une alerte s'affiche : "Seuil maximal de 50 atteint !"
- ✓ Le compteur reste à **50**

---

### ✅ Test 8 : Limites -50 (Défi 1)
**Action :**
1. Reset le compteur
2. Sélectionner pas **10**
3. Cliquer sur **-10** jusqu'à atteindre **-50**
4. Essayer de cliquer encore sur **-10**

**Résultat attendu :**
- ✓ À -50, le compteur s'arrête
- ✓ Une alerte s'affiche : "Seuil minimal de -50 atteint !"
- ✓ Le compteur reste à **-50** en rouge

---

### ✅ Test 9 : Contrôle au Clavier (Défi 3)
**Action :**
1. Reset le compteur
2. Appuyer sur la flèche **Haut (↑)** du clavier (5 fois)
3. Appuyer sur la flèche **Bas (↓)** du clavier (2 fois)

**Résultat attendu :**
- ✓ Après ↑ (5x) : compteur affiche **5**
- ✓ Après ↓ (2x) : compteur affiche **3**
- ✓ Dernière action : "Retrait de 1 (clavier)"
- ✓ L'historique contient les actions clavier

---

### ✅ Test 10 : Clavier avec Pas Variable
**Action :**
1. Reset le compteur
2. Sélectionner pas **5**
3. Appuyer sur flèche **Haut (↑)** (3 fois)

**Résultat attendu :**
- ✓ Compteur affiche **15**
- ✓ Historique : "+5, +5, +5"

---

### ✅ Test 11 : Clavier avec Limites
**Action :**
1. Mettre le compteur à **48**
2. Sélectionner pas **5**
3. Appuyer sur flèche **Haut (↑)**

**Résultat attendu :**
- ✓ Une alerte s'affiche : "Seuil maximal de 50 atteint !"
- ✓ Le compteur reste à **48**

---

### ✅ Test 12 : Chronomètre Automatique
**Action :**
1. Observer le chronomètre en bas de page
2. Attendre 5 secondes

**Résultat attendu :**
- ✓ Le chronomètre s'incrémente chaque seconde
- ✓ Affiche : "3s", puis "4s", puis "5s"...

---

### ✅ Test 13 : Pause/Reprendre du Chronomètre
**Action :**
1. Cliquer sur le bouton **Pause**
2. Attendre 3 secondes
3. Cliquer sur **Reprendre**

**Résultat attendu :**
- ✓ Après Pause : le chronomètre ne bouge plus
- ✓ Le bouton affiche "Reprendre"
- ✓ Après Reprendre : le chronomètre repart

---

### ✅ Test 14 : Démontage du Chronomètre (pas de fuite mémoire)
**Action :**
1. Ouvrir la console (F12)
2. Cliquer sur **Masquer le Chronomètre**
3. Attendre 5 secondes
4. Observer la console

**Résultat attendu :**
- ✓ Le chronomètre disparaît
- ✓ Aucun message d'erreur dans la console
- ✓ Aucun avertissement de fuite mémoire

---

### ✅ Test 15 : Remontage du Chronomètre
**Action :**
1. Cliquer sur **Afficher le Chronomètre**

**Résultat attendu :**
- ✓ Le chronomètre réapparaît
- ✓ Il redémarre à **0s**
- ✓ Il s'incrémente normalement

---

### ✅ Test 16 : Synchronisation du Titre de l'Onglet
**Action :**
1. Reset le compteur
2. Cliquer sur **+1** (7 fois)
3. Regarder le titre de l'onglet du navigateur

**Résultat attendu :**
- ✓ Le titre affiche "Compteur : 7"
- ✓ Le titre se met à jour à chaque clic

---

### ✅ Test 17 : Test Complet de Bout en Bout
**Scénario réel d'utilisation :**
1. Ouvrir l'application
2. Sélectionner pas **2**
3. Cliquer sur **+2** (10 fois) → compteur à 20
4. Utiliser la flèche **Bas (↓)** du clavier (3 fois) → compteur à 14
5. Rafraîchir la page (F5)
6. Vérifier que compteur = **14** et historique intact
7. Cliquer sur **Reset**
8. Sélectionner pas **10**
9. Essayer d'aller à 60 (devrait bloquer à 50)
10. Masquer puis réafficher le chronomètre

**Résultat attendu :**
- ✓ Toutes les étapes fonctionnent sans erreur
- ✓ Aucun rechargement de page
- ✓ Console sans erreur

---

## 🎯 Validation Finale de la Séance 5

**✅ La séance est VALIDÉE si :**
- [ ] Tous les tests 1 à 17 passent
- [ ] Les 3 défis sont fonctionnels
- [ ] Aucune erreur dans la console
- [ ] L'application est fluide et réactive

---

## 🐛 Dépannage

### Problème : Le compteur ne réagit pas aux clics
**Solution :** Vérifier que `onClick={handleIncrement}` (sans parenthèses)

### Problème : L'historique ne se sauvegarde pas
**Solution :** Vérifier `JSON.stringify()` et `JSON.parse()` dans useEffect

### Problème : Fuite mémoire avec le chronomètre
**Solution :** Vérifier la fonction cleanup `return () => clearInterval(id)`

### Problème : Le clavier ne fonctionne pas
**Solution :** Vérifier `window.removeEventListener` dans le cleanup

### Problème : Le localStorage ne fonctionne pas
**Solution :** Ouvrir en mode navigation privée peut bloquer localStorage

---

## 📊 Résumé des Fonctionnalités

| Fonctionnalité | Statut | Hook Utilisé |
|----------------|--------|--------------|
| Compteur basique | ✅ | useState |
| Pas variable | ✅ | useState |
| Couleur dynamique | ✅ | fonction pure |
| Historique | ✅ | useState (tableau) |
| Persistance compteur | ✅ | useEffect + localStorage |
| Persistance historique | ✅ | useEffect + localStorage |
| Titre onglet | ✅ | useEffect |
| Limites +50/-50 | ✅ | conditions |
| Contrôle clavier | ✅ | useEffect + cleanup |
| Chronomètre | ✅ | useEffect + setInterval |
| Pause/Reprendre | ✅ | useState |
| Démontage propre | ✅ | cleanup function |

---

**👨‍🏫 Fait par Dr. Abdelweheb GUEDDES - École Polytechnique de Sousse - 2026-2027**
