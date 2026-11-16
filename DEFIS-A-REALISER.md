# 🎖️ DÉFIS PRATIQUES EN SÉANCE - Section 7 du PDF

Les défis suivants sont à réaliser EN PLUS du Counter de base et à faire valider par l'enseignant durant la séance.

## ⭐ Défi 1 : Seuil Limite & Alerte Visuelle (useState)

### À implémenter dans Counter.jsx :

```javascript
// Dans handleIncrement :
const handleIncrement = () => {
  // AJOUT : Vérification de la limite +50
  if (count + step > 50) {
    alert('Seuil maximal de 50 atteint !');
    return; // Empêche l'opération
  }
  
  const nouveauCompte = count + step;
  setCount(nouveauCompte);
  setMessage('Ajout de ' + step);
  setTotalClics(totalClics + 1);
  const action = '+' + step;
  setHistorique([...historique, action]);
};

// Dans handleDecrement :
const handleDecrement = () => {
  // AJOUT : Vérification de la limite -50
  if (count - step < -50) {
    alert('Seuil minimal de -50 atteint !');
    return; // Empêche l'opération
  }
  
  const nouveauCompte = count - step;
  setCount(nouveauCompte);
  setMessage('Retrait de ' + step);
  setTotalClics(totalClics + 1);
  const action = '-' + step;
  setHistorique([...historique, action]);
};
```

### Test de validation :
1. Sélectionner pas 10
2. Incrémenter jusqu'à 50
3. Essayer +10 → Alerte "Seuil maximal de 50 atteint !"
4. Reset
5. Décrémenter jusqu'à -50
6. Essayer -10 → Alerte "Seuil minimal de -50 atteint !"

---

## ⭐⭐ Défi 2 : Sauvegarde & Restauration Complète de l'Historique (useEffect)

### À implémenter dans Counter.jsx :

```javascript
// 1. Modifier l'initialisation de historique :
const [historique, setHistorique] = useState(() => {
  const sauvegarde = localStorage.getItem('mon_compteur_historique');
  return sauvegarde !== null ? JSON.parse(sauvegarde) : [];
});

// 2. Ajouter un useEffect pour sauvegarder l'historique :
useEffect(() => {
  localStorage.setItem('mon_compteur_historique', JSON.stringify(historique));
}, [historique]);
```

### Test de validation :
1. Reset compteur
2. Sélectionner pas 5
3. Cliquer +5 (3 fois)
4. Historique affiche "+5, +5, +5"
5. F12 → Application → Local Storage → voir "mon_compteur_historique"
6. Refresh (F5)
7. Historique toujours "+5, +5, +5"

---

## ⭐⭐⭐ Défi 3 : Contrôle du Compteur au Clavier (useEffect & Nettoyage)

### À implémenter dans Counter.jsx :

```javascript
// Ajouter ce useEffect APRÈS tous les autres :
useEffect(() => {
  const handleKeyDown = (e) => {
    if (e.key === 'ArrowUp') {
      // Incrémenter (avec vérification de limite si Défi 1 fait)
      setCount((prev) => {
        const nouveau = prev + step;
        if (nouveau > 50) {
          alert('Seuil maximal de 50 atteint !');
          return prev; // Pas de changement
        }
        return nouveau;
      });
      setMessage('Ajout de ' + step + ' (clavier)');
      setTotalClics((prev) => prev + 1);
      setHistorique((prev) => [...prev, '+' + step]);
    } else if (e.key === 'ArrowDown') {
      // Décrémenter (avec vérification de limite si Défi 1 fait)
      setCount((prev) => {
        const nouveau = prev - step;
        if (nouveau < -50) {
          alert('Seuil minimal de -50 atteint !');
          return prev; // Pas de changement
        }
        return nouveau;
      });
      setMessage('Retrait de ' + step + ' (clavier)');
      setTotalClics((prev) => prev + 1);
      setHistorique((prev) => [...prev, '-' + step]);
    }
  };

  // Attacher l'écouteur
  window.addEventListener('keydown', handleKeyDown);

  // IMPÉRATIF : Fonction de nettoyage
  return () => {
    window.removeEventListener('keydown', handleKeyDown);
  };
}, [step]); // Dépendance : step
```

### Test de validation :
1. Reset compteur
2. Appuyer Flèche Haut (↑) 5 fois → compteur = 5
3. Appuyer Flèche Bas (↓) 2 fois → compteur = 3
4. Sélectionner pas 10
5. Flèche Haut (↑) → compteur += 10
6. Tester limite : mettre à 48, pas 5, ↑ → alerte

---

## 📋 Validation Finale de la Séance 5

**Point de contrôle final devant l'enseignant :**

☐ Les touches fléchées du clavier incrémentent le compteur  
☐ L'historique survit au refresh (F5)  
☐ Le chronomètre se démonte proprement sans fuite mémoire  
☐ Les limites +50/-50 sont respectées  
☐ Toutes les fonctionnalités fonctionnent sans rechargement de page

**✅ Séance 5 validée dès que TOUS les points sont OK !**
