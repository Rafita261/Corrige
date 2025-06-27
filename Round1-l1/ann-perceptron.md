# 🧠 Challenge V – Artificial Neural Network: Perceptron

## 📝 Énoncé

L’un des fondements de l’intelligence artificielle est le **réseau de neurones**, qui est composé d’unités interconnectées appelées **neurones**.  
Un **perceptron** est le modèle le plus simple de neurone.

Chaque neurone contient :

- Des **entrées** : `inputs`
- Des **poids** : `weights`
- Un **biais** : `bias`
- Une **fonction d’activation** : `f`
- Une **sortie** : `output`

---

## 📐 Formule de calcul

Le calcul de la sortie se fait selon la formule :

```
output = f(Σ(inputs[i] * weights[i]) + bias)
```

Ensuite, on applique une **fonction d’arrondi spéciale** pour respecter les contraintes de sortie.

---

## 🧠 Fonctions d’activation possibles

| Fonction      | Nom dans l’entrée | Description                            |
|---------------|------------------|----------------------------------------|
| Identité      | `identity`       | f(x) = x                                |
| Sigmoïde      | `sigmoid`        | f(x) = 1 / (1 + exp(-x))                |
| Heaviside     | `heaviside`      | f(x) = 0 si x < 0, sinon 1              |
| Tanh          | `tanh`           | f(x) = tanh(x)                          |
| ReLU          | `relu`           | f(x) = max(0, x)                        |

---

## 🔁 Fonction d'arrondi spéciale

Afin de coller aux contraintes du sujet, les sorties doivent être :

- Un **entier** si possible (ex. `3.00` devient `3`)
- Un **réel avec 1 ou 2 décimales significatives**
- Si le résultat est **proche de 0** (ex. `0.0009`), retourner `0`

### 🔢 Exemples d’arrondi

| Entrée        | Sortie attendue |
|---------------|-----------------|
| 1.158696      | `1.16`          |
| 2.0000        | `2`             |
| -1.9999       | `-2`            |
| 0.00092       | `0`             |
| 3.10          | `3.1`           |

---

## 📥 Format d’entrée (STDIN)

```
n              ← nombre de tests
m              ← taille des vecteurs input et weight
inputs (m)     ← m entiers
weights (m)    ← m entiers
bias           ← entier
f              ← nom de la fonction d’activation
(recommencer pour n tests)
```

---

## 📤 Format de sortie

Un entier ou réel arrondi selon les règles, pour chaque test.

---

## ✅ Exemples

### 🔢 Input
```
2
3
1 1 1
1 2 3
1
identity
2
5 6
-2 1
1
relu
```

### 🎯 Output
```
7
0
```

---

## 🐍 Implémentation en Python

```python
import math

def Round(x):
    if x == int(x) or int(x)*100 == int(x*100):
        return int(x)
    if (x*10) == int(x*10):
        return round(x, 1)
    return round(x, 2)

def perceptron(inputs, weight, bias, f, m):
    o = bias
    for i in range(m):
        o += inputs[i] * weight[i]
    if f == "sigmoid":
        return Round(1 / (1 + math.exp(-o)))
    if f == "tanh":
        return Round(math.tanh(o))
    if f == "heaviside":
        return 0 if o < 0 else 1
    if f == "relu":
        return Round(max(0, o))
    return Round(o)

if __name__ == "__main__":
    n = int(input())
    for _ in range(n):
        m = int(input())
        inputs = list(map(int, input().split()))
        weights = list(map(int, input().split()))
        bias = int(input())
        f = input().strip().lower()
        print(perceptron(inputs, weights, bias, f, m))
```

---

📂 [⬅ Retour à la liste des challenges](../)

---
